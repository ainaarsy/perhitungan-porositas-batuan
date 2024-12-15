import tkinter as tk

def hitung_porositas():
    try:
        # Ambil input pengguna
        rho_b = float(entry_rho_b.get())
        rho_s = float(entry_rho_s.get())

        # Validasi input
        if rho_b <= 0 or rho_s <= 0:
            result_label.config(text="Masukkan nilai yang valid!")
            return

        # Hitung porositas
        porositas = 1 - (rho_b / rho_s)
        porositas = porositas * 100  # Mengubah ke persen

        # Tampilkan hasil
        result_label.config(text=f"Porositas Batuan: {porositas:.2f} %")
    except ValueError:
        result_label.config(text="Masukkan angka yang valid!")

# Membuat window aplikasi
root = tk.Tk()
root.title("Perhitungan Porositas Batuan")

# Label dan entry untuk massa jenis batuan
label_rho_b = tk.Label(root, text="Massa Jenis Batuan (ρb) dalam g/cm³:")
label_rho_b.grid(row=0, column=0, padx=10, pady=5)

entry_rho_b = tk.Entry(root)
entry_rho_b.grid(row=0, column=1, padx=10, pady=5)

# Label dan entry untuk massa jenis batuan padat
label_rho_s = tk.Label(root, text="Massa Jenis Batuan Padat (ρs) dalam g/cm³:")
label_rho_s.grid(row=1, column=0, padx=10, pady=5)

entry_rho_s = tk.Entry(root)
entry_rho_s.grid(row=1, column=1, padx=10, pady=5)

# Tombol untuk menghitung
calculate_button = tk.Button(root, text="Hitung Porositas", command=hitung_porositas)
calculate_button.grid(row=2, column=0, columnspan=2, pady=10)

# Label untuk menampilkan hasil
result_label = tk.Label(root, text="Porositas Batuan: -")
result_label.grid(row=3, column=0, columnspan=2, pady=10)

# Menjalankan aplikasi
root.mainloop()
