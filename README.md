# PerhitunanDiskon
 Tugas 3-Muhammad Azhari Nur Pratama-2210010326

## 1. Deskripsi Program:
• Pengguna memasukkan harga asli dan memilih persentase diskon
• Setelah menghitung, tampilkan harga akhir dan jumlah
penghematan

## 2. Komponen GUI: 
JFrame, JPanel, JLabel, JTextField, JComboBox, JButton
## 3. Logika Program: 
Perhitungan aritmatika, Penanganan eksepsi
## 4. Events:
• ActionListener untuk tombol Hitung
~~~
private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {                                         
try {
            // Cek apakah hargaAsliTextField kosong atau tidak valid
            if (jTextField1.getText().isEmpty() || jTextField1.getText().equals("Rp ")) {
                JOptionPane.showMessageDialog(this, "Silakan masukkan harga asli.", "Error", JOptionPane.ERROR_MESSAGE);
                return;
            }
            // Ambil harga asli dari JTextField dan hilangkan "Rp " di depannya
            double hargaAsli = Double.parseDouble(jTextField1.getText().replace("Rp ", ""));

            // Tentukan diskon persentase dari JSlider atau JComboBox
            int diskonPersen;
            if (jSlider1.getValue() > 0) {
                diskonPersen = jSlider1.getValue();
            } else {
                String diskonStr = (String) jComboBox1.getSelectedItem();
                diskonPersen = Integer.parseInt(diskonStr.replace("%", ""));
            }

            // Ambil kode kupon dari JTextField
            String kodeKupon = jTextField4.getText().trim();

            // Tambahan diskon jika kode kupon valid
            if (kodeKupon.equalsIgnoreCase("DISKON10")) {
                diskonPersen += 10;
            } else if (!kodeKupon.isEmpty()) {
                JOptionPane.showMessageDialog(this, "Kode kupon tidak valid.", "Info", JOptionPane.INFORMATION_MESSAGE);
            }
            // Hitung penghematan dan harga akhir
            double penghematan = hargaAsli * diskonPersen / 100;
            double hargaAkhir = hargaAsli - penghematan;

   // Tampilkan hasil pada JTextField dengan prefix "Rp "
            jTextField2.setText("Rp " + String.format("%.2f", penghematan));
            jTextField3.setText("Rp " + String.format("%.2f", hargaAkhir));

            // Tambahkan hasil ke riwayat
            String hasilRiwayat = "Harga Asli: Rp " + hargaAsli +
                                  ", Diskon: " + diskonPersen + "%" +
                                  ", Penghematan: Rp " + String.format("%.2f", penghematan) +
                                  ", Harga Akhir: Rp " + String.format("%.2f", hargaAkhir) + "\n";
            jTextArea1.append(hasilRiwayat);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Masukkan nilai yang valid.", "Error", JOptionPane.ERROR_MESSAGE);
}
~~~
• ItemListener pada JComboBox untuk memilih persentase diskon
~~~
      initComponents();
        jComboBox1.addItem("10%");
        jComboBox1.addItem("20%");
        jComboBox1.addItem("30%");
    }
~~~
5. Variasi:
• Tambahkan opsi untuk memasukkan kode kupon diskon tambahan
~~~
if (kodeKupon.equalsIgnoreCase("DISKON10")) {
                diskonPersen += 10;
            } else if (!kodeKupon.isEmpty()) {
                JOptionPane.showMessageDialog(this, "Kode kupon tidak valid.", "Info", JOptionPane.INFORMATION_MESSAGE);
            }
   ~~~
• Tambahkan JSlider sebagai alternatif JComboBox untuk memilih persentase diskon
   ~~~
private void jSlider1StateChanged(javax.swing.event.ChangeEvent evt) {                                      
          jSlider1.addChangeListener((ChangeEvent e) -> {
    lblDiskonSlider.setText(jSlider1.getValue() + "%");
});
    } 
~~~
• Sediakan riwayat perhitungan diskon yang telah dilakukan
 ~~~
 String hasilRiwayat = "Harga Asli: Rp " + hargaAsli +
 ", Diskon: " + diskonPersen + "%" +
 ", Penghematan: Rp " + String.format("%.2f", penghematan) +
 ", Harga Akhir: Rp " + String.format("%.2f", hargaAkhir) + "\n";
 jTextArea1.append(hasilRiwayat);
 ~~~

## Hasil Setelah Di Run
![Cuplikan layar 2024-11-06 163002](https://github.com/user-attachments/assets/97f57466-43c8-4de1-88c7-2d368c4f490a)


## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    20    |
|  2  | Logika Program   |    20    |
|  3  | Kesesuaian UI    |    15    |
|  4  | Constructor      |    15    |
|  5  | Memenuhi Variasi |    30    |
|     | TOTAL        | 100 |

## Pembuat

Nama  : Muhammad Azhari Nur Pratama
NPM   : 2210010326

