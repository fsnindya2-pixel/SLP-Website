<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sertifikasi Laik Produksi Batching Plant (Multistep Form)</title>
    <link rel="stylesheet" href="./css/style.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script> 
    <script src="path/to/your/script.js"></script>
<body>

    <div class="container">
        <header>
            <h1>Pemeriksaan Kelaikan Produksi (Batching Plant)</h1>
            <p>Rancangan Aktualisasi Nindya Fitri Sari</p>
        </header>

        <div class="steps-indicator">
            <div class="step active" data-step="1">
                <span class="circle">1</span>
                Pengujian Mutu Campuran Beton Semen
            </div>
            <div class="step" data-step="2">
                <span class="circle">2</span>
                Rekapitulasi Pemeriksaan
            </div>
            <div class="step" data-step="3">
                <span class="circle">3</span>
                Validasi Pemeriksaan
            </div>
        </div>

   <!-- #region Langkah 1-->
        <form id="form-beton">
            <div id="step-1" class="form-step active">
                <section class="form-section">
                    <h2>Langkah 1: Formulir Pengujian Mutu Campuran Beton Semen</h2>
                    <table>
                        <thead>
                            <tr>
                                <th class="table-wrapper1">Pengujian</th>
                                <th class="table-wrapper2"></th>
                                <th class="table-wrapper">Mix Design</th>
                                <th class="table-wrapper">Hasil Pengukuran</th>
                                <th class="table-wrapper">Penilaian</th>
                                <th class="table-wrapper">Keterangan</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr class="group-header"><td colspan="6">Parameter Beton Segar</td></tr>
                    
                        <tr data-row="slump">
                        <td>Slump (mm)</td>
                        <td>
                            <div class="input-group1">
                                <label for="slump-min"></label>
                                <input type="number" id="slump-min" placeholder="Min.">
                            </div>
                            <div class="input-group1">
                                <label for="slump-max"></label>
                                <input type="number" id="slump-max" placeholder="Maks.">
                            </div>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for=""></label>
                                <input type="number" id="" placeholder="" >
                            </div>
                        </td>  
                        <td>
                           <div class="input-group">
                            <label for="slump-hasil"></label>
                            <input type="number" id="slump-hasil" placeholder="Hasil..."></div>
                        </td>
                        <td class="radio-group">
                            <label><input type="radio" name="slump-penilaian" value="sesuai" disabled>Sesuai</label><br>
                            <label><input type="radio" name="slump-penilaian" value="tidak" disabled>Tidak</label>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for="slump-keterangan"></label>
                                <input type="text" id="slump-keterangan" placeholder="Ket..."> 
                            </div>
                            <div class="input-group-file">
                                <label for="slump-foto" class="button-upload">Upload Foto</label>
                                <input type="file" id="slump-foto" name="slump-foto" accept="image/*" style="display: none;" data-max-size="5242880">
                                <span id="slump-foto-status" class="upload-status">Belum ada file.</span>
                                <img id="preview-slump-foto" class="uploaded-image-preview" src="" style="display:none;">
                            </div>
                        </td>
                        </tr>

                        <tr data-row="retensi-slump">
                        <td>Retensi Slump</td>
                        <td>
                            <div class="input-group1">
                                <label for="retensi-slump-max"></label>
                                <input type="number" id="retensi-slump-max" placeholder="Maks.">
                            </div>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for=""></label>
                                <input type="number" id="" placeholder="" >
                            </div>
                        </td>  
                        <td>
                           <div class="input-group">
                            <label for="retensi-slump-hasil"></label>
                            <input type="number" id="retensi-slump-hasil" placeholder="Hasil..."></div>
                        </td>
                        <td class="radio-group">
                            <label><input type="radio" name="retensi-slump-penilaian" value="sesuai" disabled>Sesuai</label><br>
                            <label><input type="radio" name="retensi-slump-penilaian" value="tidak" disabled>Tidak</label>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for="retensi-slump-keterangan"></label>
                                <input type="text" id="retensi-slump-keterangan" placeholder="Ket..."> 
                            </div>
                            <div class="input-group-file">
                                <label for="retensi-slump-foto" class="button-upload">Upload Foto</label>
                                <input type="file" id="retensi-slump-foto" name="retensi-slump-foto" accept="image/*" style="display: none;" data-max-size="5242880">
                                <span id="retensi-slump-foto-status" class="upload-status">Belum ada file.</span>
                                <img id="preview-retensi-slump-foto" class="uploaded-image-preview" src="" style="display:none;"> 
                            </div>
                        </td>

                        <tr data-row="berat">
                        <td>Berat per meter kubik yang dihitung berdasarkan bebas rongga udara (kg/m³)</td>
                        <td>
                            <div class="input-group1">
                                <label for="berat-min"></label>
                                <input type="number" id="berat-min" placeholder="Min.">
                            </div>
                            <div class="input-group1">
                                <label for="berat-max"></label>
                                <input type="number" id="berat-max" placeholder="Maks.">
                            </div>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for=""></label>
                                <input type="number" id="" placeholder="" >
                            </div>
                        </td>  
                        <td>
                           <div class="input-group">
                            <label for="berat-hasil"></label>
                            <input type="number" id="berat-hasil" placeholder="Hasil..."></div>
                        </td>
                        <td class="radio-group">
                            <label><input type="radio" name="berat-penilaian" value="sesuai" disabled>Sesuai</label><br>
                            <label><input type="radio" name="berat-penilaian" value="tidak" disabled>Tidak</label>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for="berat-keterangan"></label>
                                <input type="text" id="berat-keterangan" placeholder="Ket..."> 
                            </div>
                            <div class="input-group-file">
                                <label for="berat-foto" class="button-upload">Upload Foto</label>
                                <input type="file" id="berat-foto" name="berat-foto" accept="image/*" style="display: none;" data-max-size="5242880">
                                <span id="berat-foto-status" class="upload-status">Belum ada file.</span>
                                <img id="preview-berat-foto" class="uploaded-image-preview" src="" style="display:none;">
                            </div>
                        </td>
                        </tr>

                        <tr data-row="setting">
                        <td>Setting Time</td>
                        <td>
                            <div class="input-group1">
                                <label for="setting-max"></label>
                                <input type="number" id="setting-max" placeholder="Maks.">
                            </div>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for=""></label>
                                <input type="number" id="" placeholder="" >
                            </div>
                        </td>  
                        <td>
                           <div class="input-group">
                            <label for="setting-hasil"></label>
                            <input type="number" id="setting-hasil" placeholder="Hasil..."></div>
                        </td>
                        <td class="radio-group">
                            <label><input type="radio" name="setting-penilaian" value="sesuai" disabled>Sesuai</label><br>
                            <label><input type="radio" name="setting-penilaian" value="tidak" disabled>Tidak</label>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for="setting-keterangan"></label>
                                <input type="text" id="setting-keterangan" placeholder="Ket..."> 
                            </div>
                            <div class="input-group-file">
                                <label for="setting-foto" class="button-upload">Upload Foto</label>
                                <input type="file" id="setting-foto" name="setting-foto" accept="image/*" style="display: none;" data-max-size="5242880"> 
                                <span id="setting-foto-status" class="upload-status">Belum ada file.</span>
                                <img id="preview-setting-foto" class="uploaded-image-preview" src="" style="display:none;">
                            </div>
                            </td>
                        </tr>

                        <tr data-row="temperatur">
                        <td>Temperatur Beton Segar (°C)</td>
                        <td>
                            <div class="input-group1">
                                <label for="temperatur-max"></label>
                                <input type="number" id="temperatur-max" placeholder="Maks.">
                            </div>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for=""></label>
                                <input type="number" id="" placeholder="" >
                            </div>
                        </td>  
                        <td>
                           <div class="input-group">
                            <label for="temperatur-hasil"></label>
                            <input type="number" id="temperatur-hasil" placeholder="Hasil..."></div>
                        </td>
                        <td class="radio-group">
                            <label><input type="radio" name="temperatur-penilaian" value="sesuai" disabled>Sesuai</label><br>
                            <label><input type="radio" name="temperatur-penilaian" value="tidak" disabled>Tidak</label>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for="temperatur-keterangan"></label>
                                <input type="text" id="temperatur-keterangan" placeholder="Ket..."> 
                            </div>
                            <div class="input-group-file">
                                <label for="temperatur-foto" class="button-upload">Upload Foto</label>
                                <input type="file" id="temperatur-foto" name="temperatur-foto" accept="image/*" style="display: none;" data-max-size="5242880"> 
                                <span id="temperatur-foto-status" class="upload-status">Belum ada file.</span>
                                <img id="preview-temperatur-foto" class="uploaded-image-preview" src="" style="display:none;">
                            </div>
                        </td>
                        </tr>

                        <tr class="group-header"><td colspan="6">Parameter Beton Keras</td></tr>

                        <tr data-row="kuat-lentur">
                        <td>Kuat Lentur pada perkerasan beton semen (pengendalian produksi)</td>
                        <td>
                            <div class="input-group1">
                                <label for="kuat-lentur-min"></label>
                                <input type="number" id="kuat-lentur-min" placeholder="Min.">
                            </div>
                            <div class="input-group1">
                                <label for="kuat-lentur-max"></label>
                                <input type="number" id="kuat-lentur-max" placeholder="Maks.">
                            </div>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for=""></label>
                                <input type="number" id="" placeholder="" >
                            </div>
                        </td>  
                        <td>
                           <div class="input-group">
                            <label for="kuat-lentur-hasil"></label>
                            <input type="number" id="kuat-lentur-hasil" placeholder="Hasil..."></div>
                        </td>
                        <td class="radio-group">
                            <label><input type="radio" name="kuat-lentur-penilaian" value="sesuai" disabled>Sesuai</label><br>
                            <label><input type="radio" name="kuat-lentur-penilaian" value="tidak" disabled>Tidak</label>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for="kuat-lentur-keterangan"></label>
                                <input type="text" id="kuat-lentur-keterangan" placeholder="Ket..."> 
                            </div>
                            <div class="input-group-file">
                                <label for="kuat-lentur-foto" class="button-upload">Upload Foto</label>
                                <input type="file" id="kuat-lentur-foto" name="kuat-lentur-foto" accept="image/*" style="display: none;" data-max-size="5242880"> 
                                <span id="kuat-lentur-foto-status" class="upload-status">Belum ada file.</span>
                                <img id="preview-kuat-lentur-foto" class="uploaded-image-preview" src="" style="display:none;">
                            </div>
                        </td>
                        </tr>

                        <tr data-row="kuat-tekan">
                        <td>Kuat Tekan rata-rata pada umur 7 (tujuh) hari untuk setiap benda uji, berdasarkan kuat rata-rata dari pengujian semua benda uji yang dibandingkan, %</td>
                        <td>
                            <div class="input-group1">
                                <label for="kuat-tekan-min"></label>
                                <input type="number" id="kuat-tekan-min" placeholder="Min.">
                            </div>
                            <div class="input-group1">
                                <label for="kuat-tekan-max"></label>
                                <input type="number" id="kuat-tekan-max" placeholder="Maks.">
                            </div>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for=""></label>
                                <input type="number" id="" placeholder="" >
                            </div>
                        </td>  
                        <td>
                           <div class="input-group">
                            <label for="kuat-tekan-hasil"></label>
                            <input type="number" id="kuat-tekan-hasil" placeholder="Hasil..."></div>
                        </td>
                        <td class="radio-group">
                            <label><input type="radio" name="kuat-tekan-penilaian" value="sesuai" disabled>Sesuai</label><br>
                            <label><input type="radio" name="kuat-tekan-penilaian" value="tidak" disabled>Tidak</label>
                        </td>
                        <td>
                            <div class="input-group">
                                <label for="kuat-tekan-keterangan"></label>
                                <input type="text" id="kuat-tekan-keterangan" placeholder="Ket..."> 
                            </div>
                            <div class="input-group-file">
                                <label for="kuat-tekan-foto" class="button-upload">Upload Foto</label>
                                <input type="file" id="kuat-tekan-foto" name="kuat-tekan-foto" accept="image/*" style="display: none;" data-max-size="5242880"> 
                                <span id="kuat-tekan-foto-status" class="upload-status">Belum ada file.</span>
                                <img id="preview-kuat-tekan-foto" class="uploaded-image-preview" src="" style="display:none;">
                            </div>
                            </td>
                            </tr>
                        </tbody>
                    </table>

                    <div class="conclusion-box">
                    <h3>Kesimpulan Pemeriksaan Mutu Campuran Produksi:</h3>
                    <div class="radio-group">
                        <label><input type="radio" name="kesimpulan_mutu" value="laik" disabled>Laik</label>
                        <label><input type="radio" name="kesimpulan_mutu" value="tidak_laik" disabled>Tidak Laik</label>
                    </div>
                    <p>Catatan Pemeriksaan Pengujian Produk</p>
                    <textarea rows="4"></textarea>
                </div>
                <div class="form-actions">
                        <button type="button" id="simpanPdfBtn" style="margin-right: 10px;">Simpan ke PDF</button>
                        <button type="button" class="btn-primary next-step" data-next="step-2">Lanjut</button>
                </div>
                </section>
            </div>

<!-- #region Langkah 2-->
            <div id="step-2" class="form-step hidden">
                <section class="form-section">
                    <h2>Langkah 2: Rekapitulasi Pemeriksaan</h2>
                    
                    <table>
                        <thead>
                            <tr>
                                <th class="kolom-no">No.</th>
                                <th class="table-wrapper">Deskripsi</th>
                                <th class="kolom-penilaian">Penilaian Terhadap Kelaikan</th>
                                <th class="table-wrapper">Keterangan</th>
                            </tr>
                        </thead>
                        <tbody>
                        <tr>
                            <td class="kolom-no">1.</td>
                            <td><textarea rows="2"></textarea></td>
                            <td class="penilaian-group">
                                <label><input type="radio" name="penilaian_1" value="sesuai" class="hidden-radio">
                                <span class="penilaian-btn">Sesuai</span></label>
                                <label><input type="radio" name="penilaian_1" value="tidak" class="hidden-radio">
                                <span class="penilaian-btn">Tidak</span></label>
                            </td>
                            <td><textarea rows="2"></textarea></td>
                        </tr> 
                        <tr>
                            <td class="kolom-no">2.</td>
                            <td><textarea rows="2"></textarea></td>
                            <td class="penilaian-group">
                                <label><input type="radio" name="penilaian_2" value="sesuai" class="hidden-radio">
                                <span class="penilaian-btn">Sesuai</span></label>
                                <label><input type="radio" name="penilaian_2" value="tidak" class="hidden-radio">
                                <span class="penilaian-btn">Tidak</span></label>
                            </td>
                            <td><textarea rows="2"></textarea></td>
                        </tr> 
                        <tr>
                            <td class="kolom-no">3.</td>
                            <td><textarea rows="2"></textarea></td>
                            <td class="penilaian-group">
                                <label><input type="radio" name="penilaian_3" value="sesuai" class="hidden-radio">
                                <span class="penilaian-btn">Sesuai</span></label>
                                <label><input type="radio" name="penilaian_3" value="tidak" class="hidden-radio">
                                <span class="penilaian-btn">Tidak</span></label>
                            </td>
                            <td><textarea rows="2"></textarea></td>
                        </tr> 
                        <tr>
                            <td class="kolom-no">4.</td>
                            <td><textarea rows="2"></textarea></td>
                            <td class="penilaian-group">
                                <label><input type="radio" name="penilaian_4" value="sesuai" class="hidden-radio">
                                <span class="penilaian-btn">Sesuai</span></label>
                                <label><input type="radio" name="penilaian_4" value="tidak" class="hidden-radio">
                                <span class="penilaian-btn">Tidak</span></label>
                            </td>
                            <td><textarea rows="2"></textarea></td>
                        </tr> 
                        <tr>
                            <td class="kolom-no">5.</td>
                            <td><textarea rows="2"></textarea></td>
                            <td class="penilaian-group">
                                <label><input type="radio" name="penilaian_5" value="sesuai" class="hidden-radio">
                                <span class="penilaian-btn">Sesuai</span></label>
                                <label><input type="radio" name="penilaian_5" value="tidak" class="hidden-radio">
                                <span class="penilaian-btn">Tidak</span></label>
                            </td>
                            <td><textarea rows="2"></textarea></td>
                        </tr> 
                        </tbody>
                    </table>

                    <div style="text-align: right; margin-top: 10px;">
                        <button type="button" id="tambah-baris-rekap" class="btn-secondary">
                            + Tambah Baris
                        </button>
                    </div>

                    <div class="section-title">
                        <u>Catatan Pemeriksa Peralatan Pencampur Beton Semen (Batching Plant):</u>
                    </div>
                    <div class="notes-area">
                        <textarea rows="5" placeholder="Masukkan catatan pemeriksaan di sini..."></textarea>
                    </div>
                    <div class="section-title summary-title">
                        <u>Kesimpulan dan Saran Pemeriksa:</u>
                    </div>

                    <table class="summary-table">
                    <tbody>
                        <tr>
                            <td class="kolom-no">1.</td>
                            <td class="description-cell">Harus Diperbaiki Tahap III<br>(terhadap komponen yang rusak)</td>
                            <td class="checkbox-cell">
                                <input type="checkbox" name="kesimpulan_1" id="kesimpulan_1">
                                <label for="kesimpulan_1" class="custom-checkbox"></label>
                            </td>
                        </tr>
                        <tr>
                            <td class="kolom-no">2.</td>
                            <td class="description-cell">Laik Produksi</td>
                            <td class="checkbox-cell">
                                <input type="checkbox" name="kesimpulan_2" id="kesimpulan_2">
                                <label for="kesimpulan_2" class="custom-checkbox"></label>
                            </td>
                        </tr>
                    </tbody>
                    </table>

                    <div class="form-actions">
                        <button type="button" class="btn-secondary prev-step" data-prev="step-1"> &laquo; Kembali</button>
                        <button type="button" class="btn-primary next-step" data-next="step-3">Lanjut</button>
                    </div>

                </section>
            </div>

<!-- #region Langkah 3-->
            <div id="step-3" class="form-step hidden">
                <section class="form-section">
                    <h2>Langkah 3: Validasi Pemeriksaan</h2>
                            
                    <div class="signature-block">
                        <h3>Petugas Pemeriksa</h3>
                        <table class="signature-table">
                            <thead>
                                <tr>
                                    <th class="table-wrapper">Nama</th>
                                    <th class="table-wrapper">Jabatan</th>
                                    <th class="table-wrapper">Tanggal</th>
                                    <th class="table-wrapper">Tanda Tangan</th>
                                </tr>
                            </thead>
                            <tbody>
                                    <tr>
                                    <td><input type="text" name="pemeriksa_nama" placeholder="Nama Lengkap"></td>
                                    <td><input type="text" name="pemeriksa_jabatan" placeholder="Jabatan Pemeriksa"></td>
                                    <td><input type="date" name="pemeriksa_tanggal"></td>
                                    <td>
                                    <div class="ttd-container">
                                        <button type="button" class="ttd-btn" data-ttd-for="ttdCanvas1">Input</button>
                                        <input type="hidden" id="ttdData1" name="tanda_tangan_1">
                                        <img id="ttdPreview1" class="ttd-preview" style="max-width: 100px; display: none;">
                                    </div>
                                    <div id="ttdModal" class="modal">
                                        <div class="modal-content">
                                            <span class="close-btn">&times;</span>
                                            <h3>Tanda Tangan Digital</h3>
                                            <canvas id="ttdCanvas" width="400" height="150" style="border: 1px solid #000;"></canvas>
                                            <div class="modal-actions">
                                                <button type="button" id="clearTtdBtn">Bersihkan</button>
                                                <button type="button" id="saveTtdBtn">Simpan TTD</button>
                                            </div>
                                        </div>
                                    </div>
                                    </td>
                                    </tr>

                                    <tr>
                                    <td><input type="text" name="pemeriksa_nama" placeholder="Nama Lengkap"></td>
                                    <td><input type="text" name="pemeriksa_jabatan" placeholder="Jabatan Pemeriksa"></td>
                                    <td><input type="date" name="pemeriksa_tanggal"></td>
                                    <td>
                                    <div class="ttd-container">
                                        <button type="button" class="ttd-btn" data-ttd-for="ttdCanvas1">Input</button>
                                        <input type="hidden" id="ttdData1" name="tanda_tangan_1">
                                        <img id="ttdPreview1" class="ttd-preview" style="max-width: 100px; display: none;">
                                    </div>
                                    <div id="ttdModal" class="modal">
                                        <div class="modal-content">
                                            <span class="close-btn">&times;</span>
                                            <h3>Tanda Tangan Digital</h3>
                                            <canvas id="ttdCanvas" width="400" height="150" style="border: 1px solid #000;"></canvas>
                                            <div class="modal-actions">
                                                <button type="button" id="clearTtdBtn">Bersihkan</button>
                                                <button type="button" id="saveTtdBtn">Simpan TTD</button>
                                            </div>
                                        </div>
                                    </div>
                                    </td>
                                    </tr>
                            </tbody>
                        </table>
                    </div>
                </section>

                    <div class="form-actions">
                        <button type="button" class="btn-secondary prev-step" data-prev="step-2"> &laquo; Kembali</button>
                        <button type="submit" class="btn-primary">Selesai &amp; Kirim</button>
                    </div>
                </section>
            </div>
        </form>
    </div>

    <script src="script.js"></script>
</body>
</html>
