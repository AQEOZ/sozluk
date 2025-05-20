import tkinter as tk
from tkinter import PhotoImage, Label



sayi = 123
isim = "Ahmet"
notlar = [90, 85, 100]

# Arayüz
arayüz = tk.Tk()
arayüz.attributes("-fullscreen",True)
arayüz.bind("<Escape>", lambda e: arayüz.attributes('-fullscreen', False))
arayüz.title("AQOEZ KÜÜPHANESİ")
arayüz.geometry("1700x1700")
arayüz.configure(bg="red")

# İkon (varsa)
try:
    arayüz.iconbitmap("ikonum.ico.ico")  # Gerçekten varsa etkinleşir
except Exception as e:
    print("İkon yüklenemedi:", e)

# Giriş alanı
y = tk.StringVar()
kullanıcı_girisi = tk.Entry(arayüz, textvariable=y, font=("Arial", 14), width=40)
kullanıcı_girisi.place(x=455, y=320)

# Sonuç etiketi
sonuc_etiketi = tk.Label(arayüz, text="", font=("Arial", 12), bg="red", fg="white")
sonuc_etiketi.place(x=455, y=370)

# ARA butonu
def ARA_komut():
    var_adi = y.get().strip()
    if var_adi in globals():
        deger = globals()[var_adi]
        sonuc_etiketi.config(text=f"Sonuç: {deger}")
    else:
        sonuc_etiketi.config(text="Sonuç bulunamadı.")

ARA = tk.Button(arayüz, text="ARA", command=ARA_komut)
ARA.place(x=905, y=320)

# Pixel art görseli (renkli olan PNG gösteriliyor)
try:
    pixel_art = PhotoImage(file="B.png")
    resim_etiketi = Label(arayüz, image=pixel_art, bg="red")
    resim_etiketi.image = pixel_art  # referansı tut
    resim_etiketi.place(x=520, y=0)
except Exception as e:
    print("Resim yüklenemedi:", e)

arayüz.mainloop()
