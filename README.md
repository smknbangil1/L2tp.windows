Agar Windows bisa terhubung ke **L2TP/IPsec VPN Server**, ikuti langkah-langkah berikut:  

---

## **A. Konfigurasi VPN di Windows**  
### **Langkah 1: Tambah Koneksi VPN**  
1. Buka **Settings** (Windows + I) → **Network & Internet** → **VPN**.  
2. Klik **Add a VPN Connection**.  
3. Isi pengaturan:  
   - **VPN Provider**: `Windows (built-in)`  
   - **Connection Name**: `VPN L2TP` (bebas)  
   - **Server name or address**: Masukkan **IP publik server** contoh: 101.255.118.254 
   - **VPN type**: `L2TP/IPsec with pre-shared key`  
   - **Pre-shared key**: Masukkan **ipsec-secret** (misalnya: `Rahasia`)  
   - **Type of sign-in info**: `User name and password`  
   - **User name**: `Laptop01` (sesuai konfigurasi server)  
   - **Password**: `Laptop01`  

4. Klik **Save**.  

---

### **Langkah 2: Atur Properti Koneksi VPN**  
1. Klik koneksi **VPN L2TP** yang baru dibuat → **Advanced options** → **Edit adapter options**.  
2. Klik kanan koneksi VPN → **Properties**.  
3. Pergi ke tab **Security**, ubah:  
   - **Type of VPN** → `Layer 2 Tunneling Protocol with IPsec (L2TP/IPsec)`.  
   - **Data encryption** → `Require encryption (disconnect if server declines)`.  
   - **Authentication** → Centang **Allow these protocols** dan pilih:  
     - `Microsoft CHAP Version 2 (MS-CHAP v2)`.  
4. Pergi ke tab **Networking**, pastikan hanya **Internet Protocol Version 4 (TCP/IPv4)** yang dicentang.  
5. Klik **OK**.  

---

### **Langkah 3: Terhubung ke VPN**  
1. Kembali ke **Settings → Network & Internet → VPN**.  
2. Pilih koneksi **VPN L2TP** → Klik **Connect**.  
3. Jika berhasil, status akan berubah menjadi **Connected**.  

---

## Troubleshot jika tidak dapat terhubung
### **Cek Windows**  
- **Registry Fix** (Jika Windows 10/11 tidak bisa konek)  
  1. Buka `regedit` (Windows + R → ketik `regedit` → Enter).  
  2. Masuk ke `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PolicyAgent`.  
  3. Klik kanan, **New → DWORD (32-bit) Value**.  
  4. Beri nama: **AssumeUDPEncapsulationContextOnSendRule**  
  5. Ubah valuenya menjadi **2**.  
  6. Restart komputer.  

Setelah itu coba konek lagi. 🚀
