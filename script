document.addEventListener('DOMContentLoaded', () => {
    // =======================================================
    // === VARIABEL DAN ELEMEN UTAMA FORMULIR MULTI-LANGKAH ===
    // =======================================================
    const nextButtons = document.querySelectorAll('.next-step');
    const prevButtons = document.querySelectorAll('.prev-step');
    const stepIndicators = document.querySelectorAll('.steps-indicator .step');
    const rows = document.querySelectorAll('tbody tr[data-row]');

    // START: TAMBAHAN UNTUK TAMBAH BARIS
    const tombolTambahBaris = document.getElementById('tambah-baris-rekap');
    const tabelBodyRekap = document.querySelector('#step-2 table tbody');
    // END: TAMBAHAN UNTUK TAMBAH BARIS

    // === ELEMEN KESIMPULAN OTOMATIS (LANGKAH 1) ===
    const radioKesimpulanLaik = document.querySelector('input[name="kesimpulan_mutu"][value="laik"]');
    const radioKesimpulanTidakLaik = document.querySelector('input[name="kesimpulan_mutu"][value="tidak_laik"]');
    // Asumsi tombol "Baik/Tidak Baik" pada Kesimpulan Langkah 1 memiliki ID ini
    const btnBaik = document.getElementById('btn-kesimpulan-baik'); 
    const btnTidakBaik = document.getElementById('btn-kesimpulan-tidakbaik'); 
    // ===========================================

    // START: PENAMBAHAN UNTUK KONTROL TOMBOL LANJUT & PDF
    const tombolLanjutLangkah1 = document.querySelector('[data-next="step-2"]'); // Pilih tombol 'Lanjut' di Langkah 1
    const tombolSimpanPDFLangkah1  = document.getElementById('simpanPdfBtn'); // Asumsi tombol Simpan ke PDF adalah tombol pertama di div action
    // END: PENAMBAHAN UNTUK KONTROL TOMBOL LANJUT & PDF

    // ===========================================
    
    // ===========================================
    // === VARIABEL DAN ELEMEN TANDA TANGAN (TTD) ===
    // ===========================================
    const ttdModal = document.getElementById('ttdModal');
    const closeBtn = document.querySelector('.close-btn');
    const ttdCanvas = document.getElementById('ttdCanvas');
    const clearTtdBtn = document.getElementById('clearTtdBtn');
    const saveTtdBtn = document.getElementById('saveTtdBtn');

    // Pastikan elemen kanvas ada sebelum mencoba mendapatkan konteks
    const ctx = ttdCanvas ? ttdCanvas.getContext('2d') : null;

    let currentTtdId = null; // Menyimpan ID kanvas yang sedang diisi (cth: 'ttdCanvas1')
    let isDrawing = false;
    
    if (ctx) {
        ctx.lineWidth = 2;
        ctx.lineCap = 'round';
        ctx.strokeStyle = '#000'; // Warna tinta
    }
    // ===========================================

    // === TAMBAHKAN FUNGSI NORMALISASI DI SINI ===
    function normalizeRowName(rowName) {
        if (!rowName) return '';
        return rowName.toLowerCase().replace(/[^a-z0-9]+/g, '-').replace(/^-|-$/g, '');
    }

    // === FUNGSI TAMBAHAN UNTUK CETAK KE PDF ===
    function printFormToPdf() {
        // Fungsi ini memicu dialog Cetak browser (yang memungkinkan 'Simpan sebagai PDF')
        window.print();
    }
    // ===========================================

    // Fungsi untuk memperbarui indikator langkah
    const updateIndicators = (currentStepId) => {
        const currentStepNumber = parseInt(currentStepId.replace('step-', ''));
        stepIndicators.forEach(indicator => {
            const indicatorStep = parseInt(indicator.dataset.step);
            if (indicatorStep === currentStepNumber) {
                indicator.classList.add('active');
            } else {
                indicator.classList.remove('active');
            }
        });
    };

    // Handler untuk tombol Lanjut
    nextButtons.forEach(button => {
        button.addEventListener('click', (e) => {
            const currentStep = e.target.closest('.form-step');
            const nextStepId = button.dataset.next;
            const nextStep = document.getElementById(nextStepId);

            if (nextStep) {
                currentStep.classList.add('hidden');
                nextStep.classList.remove('hidden');
                updateIndicators(nextStepId);
            }
        });
    });

    // Handler untuk tombol Kembali
    prevButtons.forEach(button => {
        button.addEventListener('click', (e) => {
            const currentStep = e.target.closest('.form-step');
            const prevStepId = button.dataset.prev;
            const prevStep = document.getElementById(prevStepId);

            if (prevStep) {
                currentStep.classList.add('hidden');
                prevStep.classList.remove('hidden');
                updateIndicators(prevStepId);
            }
        });
    });

    // --- FUNGSI 2: TAMBAH BARIS DINAMIS UNTUK REKAPITULASI (LANGKAH 2) ---
    function tambahBarisRekap() {
        if (!tabelBodyRekap) {
            console.error("Tabel body untuk Langkah 2 tidak ditemukan.");
            return;
        }

        const barisTerakhir = tabelBodyRekap.querySelector('tr:last-child');
        if (!barisTerakhir) return;

        const barisBaru = barisTerakhir.cloneNode(true);
        const teksNomorLama = barisTerakhir.querySelector('td:first-child').textContent.replace('.', '').trim();
        const nomorBarisLama = parseInt(teksNomorLama.match(/\d+/)) || 0;
        const nomorBarisBaru = nomorBarisLama + 1;

        barisBaru.querySelector('td:first-child').textContent = `${nomorBarisBaru}.`;

        barisBaru.querySelectorAll('textarea, input[type="radio"]').forEach((input) => {
            if (input.tagName === 'TEXTAREA') {
                input.value = '';
            }
            if (input.type === 'radio') {
                input.name = `penilaian_${nomorBarisBaru}`;
                input.checked = false;
            }
        });

        tabelBodyRekap.appendChild(barisBaru);
        barisBaru.scrollIntoView({ behavior: 'smooth', block: 'end' });
    }
    if (tombolTambahBaris) {
        tombolTambahBaris.addEventListener('click', tambahBarisRekap);
    }

    // --- FUNGSI 3: PENILAIAN OTOMATIS  (LANGKAH 1) ---      
    function checkRowValue(rowName) {
        const normalizedRowName = normalizeRowName(rowName);
        const minInput = document.getElementById(`${normalizedRowName}-min`);
        const maxInput = document.getElementById(`${normalizedRowName}-max`);
        const hasilInput = document.getElementById(`${normalizedRowName}-hasil`);

        if (!maxInput || !hasilInput) return;

        const radioSesuai = document.querySelector(`input[name="${normalizedRowName}-penilaian"][value="sesuai"]`);
        const radioTidak = document.querySelector(`input[name="${normalizedRowName}-penilaian"][value="tidak"]`);

        const min = minInput ? parseFloat(minInput.value) : NaN;
        const max = parseFloat(maxInput.value);
        const hasil = parseFloat(hasilInput.value);

        if (isNaN(hasil) || isNaN(max)) {
            if (radioSesuai) radioSesuai.checked = false;
            if (radioTidak) radioTidak.checked = false;
            updateKesimpulanOtomatis(); 
            return;
        }
        let isSesuai = false;
        const minValid = minInput && !isNaN(min);

        if (minValid) {
            isSesuai = (hasil >= min && hasil <= max);
        } else {
            isSesuai = (hasil <= max);
        }

        if (radioSesuai && radioTidak) {
            radioSesuai.checked = isSesuai;
            radioTidak.checked = !isSesuai;
        }

        updateKesimpulanOtomatis();
    }
    
    // --- FUNGSI 4: KESIMPULAN OTOMATIS (LAIK / TIDAK LAIK) (LANGKAH 1) ---
    function updateKesimpulanOtomatis() {
        if (!radioKesimpulanLaik || !radioKesimpulanTidakLaik) return;
        let semuaSesuai = true;
        let semuaTerisi = true;
        const semuaGrupPenilaian = document.querySelectorAll('#step-1 .radio-group');
        const semuaBaris = document.querySelectorAll('tbody tr[data-row]');

        // 1. Cek Kelengkapan Input "Hasil Pengukuran"
        for (const row of semuaBaris) {
            const rowName = row.dataset.row;
            const normalizedRowName = normalizeRowName(rowName);
            const hasilInput = document.getElementById(`${normalizedRowName}-hasil`);

            if (!hasilInput || hasilInput.value.trim() === '') {
                semuaTerisi = false;
                break;
            }
        }

        // 2. Cek Hasil Penilaian
        if (semuaTerisi) {
            for (const grup of semuaGrupPenilaian) {
                const radioSesuai = grup.querySelector('input[value="sesuai"]');
                const radioTidak = grup.querySelector('input[value="tidak"]');

                if (radioTidak && radioTidak.checked) {
                    semuaSesuai = false;
                    break;
                }
                
                if ((radioSesuai && !radioSesuai.checked) && (radioTidak && !radioTidak.checked)) {
                    semuaSesuai = false;
                    break;
                }
            }
        }
        
        // 3. Tentukan Kesimpulan dan Kontrol Tombol
        if (!semuaTerisi) {
            radioKesimpulanLaik.checked = false;
            radioKesimpulanTidakLaik.checked = false;
        } else if (semuaSesuai) {
            radioKesimpulanLaik.checked = true;
            radioKesimpulanTidakLaik.checked = false;
        } else {
            radioKesimpulanLaik.checked = false;
            radioKesimpulanTidakLaik.checked = true;
        }
        
        // Kontrol tombol Kesimpulan Langkah 1 (jika menggunakan elemen <button>)
        if (btnBaik && btnTidakBaik) {
            if (!semuaTerisi) {
                btnBaik.setAttribute('disabled', 'disabled');
                btnTidakBaik.setAttribute('disabled', 'disabled');
            } else {
                btnBaik.removeAttribute('disabled');
                btnTidakBaik.removeAttribute('disabled');
            }
        }

        // START: LOGIKA KONTROL TOMBOL LANJUT & SIMPAN PDF
        if (tombolLanjutLangkah1 && tombolSimpanPDFLangkah1) {
            if (radioKesimpulanTidakLaik.checked) {
                // 1. Matikan tombol Lanjut
                tombolLanjutLangkah1.setAttribute('disabled', 'disabled');
                tombolLanjutLangkah1.style.opacity = '0.5'; 
                tombolLanjutLangkah1.style.cursor = 'not-allowed';

                // 2. Beri visual agar Simpan PDF dipilih (Opsional: Tambahkan class CSS 'highlight-pdf')
                if (tombolSimpanPDFLangkah1) {
                    tombolSimpanPDFLangkah1.classList.add('highlight-pdf');
                }
            } else {
                // 3. Aktifkan kembali tombol Lanjut
                tombolLanjutLangkah1.removeAttribute('disabled');
                tombolLanjutLangkah1.style.opacity = '1';
                tombolLanjutLangkah1.style.cursor = 'pointer';

                // Hapus penyorotan pada tombol Simpan PDF
                if (tombolSimpanPDFLangkah1) {
                    tombolSimpanPDFLangkah1.classList.remove('highlight-pdf');
                }
            }
        }
        // END: LOGIKA KONTROL TOMBOL LANJUT & SIMPAN PDF
    }

    // ===========================================
    // === FUNGSI LOGIKA TANDA TANGAN DIGITAL (TTD) ===
    // ===========================================
    
    // Cek apakah elemen TTD ada sebelum menjalankan logika TTD
    if (ttdCanvas && ctx) {
        
        // Fungsi untuk inisialisasi/membersihkan kanvas
        function initializeCanvas() {
            ctx.clearRect(0, 0, ttdCanvas.width, ttdCanvas.height);
            ctx.fillStyle = '#ffffff';
            ctx.fillRect(0, 0, ttdCanvas.width, ttdCanvas.height);
        }

        // === LOGIKA MENGGAMBAR (Mouse & Touch Events) ===
        function getCanvasPoint(e) {
            const rect = ttdCanvas.getBoundingClientRect();
            const clientX = e.clientX || e.touches[0].clientX;
            const clientY = e.clientY || e.touches[0].clientY;
            const x = (clientX - rect.left) * (ttdCanvas.width / rect.width);
            const y = (clientY - rect.top) * (ttdCanvas.height / rect.height);
            return { x, y };
        }

        function startDrawing(e) {
            isDrawing = true;
            const point = getCanvasPoint(e);
            ctx.beginPath();
            ctx.moveTo(point.x, point.y);
        }

        function draw(e) {
            if (!isDrawing) return;
            e.preventDefault(); 
            const point = getCanvasPoint(e);
            ctx.lineTo(point.x, point.y);
            ctx.stroke();
        }

        function stopDrawing() {
            if (isDrawing) {
                ctx.closePath();
                isDrawing = false;
            }
        }

        // Listeners untuk Menggambar
        ttdCanvas.addEventListener('mousedown', startDrawing);
        ttdCanvas.addEventListener('mousemove', draw);
        ttdCanvas.addEventListener('mouseup', stopDrawing);
        ttdCanvas.addEventListener('mouseout', stopDrawing);
        ttdCanvas.addEventListener('touchstart', startDrawing);
        ttdCanvas.addEventListener('touchmove', draw);
        ttdCanvas.addEventListener('touchend', stopDrawing);

        // === LOGIKA KONTROL MODAL ===

        // 1. Membuka Modal
        document.querySelectorAll('.ttd-btn').forEach(button => {
            button.addEventListener('click', (e) => {
                currentTtdId = e.target.getAttribute('data-ttd-for'); // Cth: 'ttdCanvas1'
                if (ttdModal) {
                    ttdModal.style.display = 'block';
                    initializeCanvas();
                }
            });
        });

        // 2. Menutup Modal
        if (closeBtn) {
            closeBtn.addEventListener('click', () => {
                ttdModal.style.display = 'none';
                currentTtdId = null;
            });
        }

        window.addEventListener('click', (e) => {
            if (e.target === ttdModal) {
                ttdModal.style.display = 'none';
                currentTtdId = null;
            }
        });

        // 3. Tombol Bersihkan
        if (clearTtdBtn) {
            clearTtdBtn.addEventListener('click', initializeCanvas);
        }

        // 4. Tombol Simpan TTD
        if (saveTtdBtn) {
            saveTtdBtn.addEventListener('click', () => {
                const ttdDataURL = ttdCanvas.toDataURL('image/png'); 
                
                // Cari input hidden dan preview image yang sesuai
                const hiddenInputId = currentTtdId.replace('Canvas', 'Data');
                const hiddenInput = document.getElementById(hiddenInputId);
                const previewImgId = currentTtdId.replace('Canvas', 'Preview');
                const previewImg = document.getElementById(previewImgId);
                const ttdButton = document.querySelector(`.ttd-btn[data-ttd-for="${currentTtdId}"]`);

                if (hiddenInput) {
                    hiddenInput.value = ttdDataURL;
                }
                
                if (previewImg) {
                    previewImg.src = ttdDataURL;
                    previewImg.style.display = 'inline';
                    if (ttdButton) ttdButton.textContent = 'Ubah TTD'; 
                }
                
                ttdModal.style.display = 'none';
                currentTtdId = null;
                alert('Tanda tangan berhasil disimpan.');
            });
        }
        
        // Inisialisasi kanvas saat dimuat
        initializeCanvas(); 
    }
    // ===========================================
    // === INITIALIZATION & EVENT LISTENERS FORMULIR ===
    // ===========================================

    // Tambahkan event listener ke setiap input yang relevan (min, max, hasil)
    rows.forEach(row => {
        const rowName = row.dataset.row;
        const maxInput = document.getElementById(`${rowName}-max`);
        const minInput = document.getElementById(`${rowName}-min`);
        const hasilInput = document.getElementById(`${rowName}-hasil`);
        const listener = () => checkRowValue(rowName);

        if (hasilInput) {
            hasilInput.addEventListener('input', listener);
        }
        if (maxInput) {
            maxInput.addEventListener('input', listener);
        }
        if (minInput) {
            minInput.addEventListener('input', listener);
        }
    });

    // ===========================================
    // === KONTROL TOMBOL SUBMIT/KIRIM (Langkah 3) ===
    // ===========================================
    const submitButton = document.querySelector('button[type="submit"]');

    if (submitButton) {
        submitButton.addEventListener('click', (e) => {
            // HENTIKAN proses pengiriman form sementara (untuk debugging/demo)
            // Hapus baris ini jika Anda ingin data dikirim ke server!
            // e.preventDefault(); 
            
            // Lakukan validasi terakhir di sini (opsional)

            // Panggil fungsi cetak/simpan PDF
            printFormToPdf();
            
            // Opsi: Tambahkan delay sebentar sebelum submit form
            // (jika Anda ingin formulir dikirim setelah cetak)
            // setTimeout(() => { e.target.closest('form').submit(); }, 500);
        });
    }

    // Logika untuk menampilkan semua step saat mencetak (agar Langkah 2 dan 3 terlihat)
    window.addEventListener('beforeprint', function() {
        // Tampilkan semua langkah formulir
        const formSteps = document.querySelectorAll('.form-step');
        formSteps.forEach(step => {
            step.classList.add('print-visible');
        });

        // Sembunyikan semua tombol dan elemen input/interaktif (diatur di CSS)
    });

    window.addEventListener('afterprint', function() {
        // Sembunyikan kembali langkah yang sebelumnya tersembunyi
        const formSteps = document.querySelectorAll('.form-step');
        formSteps.forEach(step => {
             // Hapus class print-visible jika Anda ingin mengembalikan tampilan awal
             step.classList.remove('print-visible');
        });
    });

    // Jalankan semua pengecekan saat halaman pertama kali dimuat
    updateIndicators('step-1');
    rows.forEach(row => {
        checkRowValue(row.dataset.row);
    });

 // 2. Logika Upload Foto (Inti dari permintaan Anda)
    const fileInputs = document.querySelectorAll('input[type="file"]');
    
    fileInputs.forEach(input => {
        input.addEventListener('change', function() {
            // Ambil ID baris (misalnya 'slump-foto')
            const inputId = this.id;
            // Dapatkan elemen status (span) yang sesuai (misalnya 'slump-foto-status')
            const statusElement = document.getElementById(inputId + '-status');
            // Dapatkan elemen preview gambar (misalnya 'preview-slump-foto')
            const previewElement = document.getElementById('preview-' + inputId);

            if (this.files && this.files[0]) {
                const file = this.files[0];
                const fileName = file.name;
                const maxSize = parseInt(this.getAttribute('data-max-size')); // Contoh: 5242880 bytes (5MB)

                // a. Pengecekan Ukuran File
                if (file.size > maxSize) {
                    statusElement.textContent = `Gagal! Ukuran > ${maxSize / 1024 / 1024} MB.`;
                    statusElement.style.color = 'red';
                    previewElement.style.display = 'none';
                    return;
                }
                
                // b. Update Status Menjadi "Foto diupload"
                statusElement.textContent = 'Foto diupload: ' + fileName;
                statusElement.style.color = 'green';
                
                // c. Tampilkan Preview Foto
                const reader = new FileReader();
                reader.onload = function(e) {
                    previewElement.src = e.target.result;
                    previewElement.style.display = 'block';
                };
                reader.readAsDataURL(file);

            } else {
                // Ketika file dibatalkan atau dihapus
                statusElement.textContent = 'Belum ada file.';
                statusElement.style.color = '';
                previewElement.style.display = 'none';
                previewElement.src = '';
            }
        });
    });  
    
function simpanLangkah1KePdf() {
    // 1. Targetkan elemen utama Langkah 1
    const element = document.getElementById('step-1');
    if (!element) {
        console.error('Elemen #step-1 tidak ditemukan.');
        return;
    }

    // 2. Sembunyikan elemen interaktif yang tidak diinginkan di PDF
    const elementsToHide = element.querySelectorAll('.form-actions, .input-group-file, .button-upload, input[type="file"], .uploaded-image-preview');
    elementsToHide.forEach(el => el.classList.add('hide-for-pdf'));
    
    // (Anda harus menambahkan CSS untuk class 'hide-for-pdf')

    // 3. Konfigurasi dan Konversi
    const options = {
        margin: 10,
        filename: 'Langkah1_PengujianMutu_Beton.pdf',
        image: { type: 'jpeg', quality: 0.98 },
        html2canvas: { 
            scale: 2, 
            scrollY: 0,
            useCORS: true 
        },
        jsPDF: { unit: 'mm', format: 'a4', orientation: 'portrait' }
    };

    // Panggil fungsi konversi dan simpan
    html2pdf().set(options).from(element).save().then(() => {
        // Setelah selesai (PDF didownload), tampilkan kembali elemen yang disembunyikan
        elementsToHide.forEach(el => el.classList.remove('hide-for-pdf'));
    });
}

// ===============================================
// === HUBUNGKAN FUNGSI KE TOMBOL BARU ===
// ===============================================
const simpanPdfBtn = document.getElementById('simpanPdfBtn');

if (simpanPdfBtn) {
    simpanPdfBtn.addEventListener('click', simpanLangkah1KePdf);
}

});
