# Translator
1. Program został stworzony, aby uczyć użytkownika języka angielskiego. Zadaniem użytkownika jest wybranie 1 z 4 poziomów, który mu odpowiada.
   Poziom Latwy - użytkownik musi wybrać 1 z 6 odpowiednich odpowiedzi.
   Poziom Średni - użytkownik musi wybrać 1 z 8 odpowiednich odpowiedzi.
   Poziom Średnio-trudny - W poziome srednio-trudny użytkownik będzie musiał uzupełnicz brakujących samoglosek.
   Poziom trudny - Użytkownikowi pojawa się napis w języku polskim. Użytkownik wpisuje cały wyraz.
   Po zakończenia programu wyświetla wynik w zależności od liczby uzyskanych punktów.

2. Aby włączyć program, należy najpierw pobrać biblioteki: customtkinter, mysql.connector, deep_translator, pillow.
   Trzeba włączyć xampp, dla bazy danych

3. Jest program „Database-installer” który tworzy bazę danych w folderze „Database”, na podstawie pliku SQL.

4. W folderze „Databese” znajdują bazy danych i pytania.
   W folderze „Difficulties” znajdują się poziomy trudności.
   W folderze „Images” znajdują się fotografji.
   W folderze „Textures” znajdują się fotografji dla ikony.
   
   
6. Opis
   „Quadrolingers.py”
```
      if sys.argv:
       filepath = sys.argv[0]
       folder, filename = os.path.split(filepath)
       os.chdir(folder) # now your working dir is the parent folder of the script
   sys.path.append("Database")
   sys.path.append("Images")
   sys.path.append("Textures")
   sys.path.append("Difficulties")
```
#określa lokalizację plików w folderze.
```
def start():
    window.destroy()
    from Easy import windowgra
def start2():
    window.destroy()
    from Normal import windowgra
def start3():
    window.destroy()
    from NormalHard import windowgra
def start4():
    window.destroy()
    from Hard import windowgra
def exit():
    window.destroy()
```
### Po kliknięciu w wybrany poziom trudności zostanie zaimportowany plik z wybranym poziomem trudności.


### Następnie następuje część graficzna.



# Opis
„Poziomów trudności”


```
def test(x):
    global ilosc_pytan_odpowiedzialnych
    global wylosowane_slowo
    global wylosowane_slowo_en
    global folder
    global zycia
    if x == wylosowane_slowo_en.get():
        btn1.configure(state = E) # E = Enabled
        btn2.configure(state = E)
        btn3.configure(state = E)
        btn4.configure(state = E)
        btn5.configure(state = E)
        btn6.configure(state = E)
        wylosowane_slowo = random.choice(pytania)
        pytania.remove(wylosowane_slowo)
        wylosowane_slowo_pl.set(wylosowane_slowo)
        wylosowane_slowo_en.set(GoogleTranslator(source='pl', target='en').translate(wylosowane_slowo))
        zmien()
        my_image.configure(light_image=Image.open(folder+"\Images\\"+str(wylosowane_slowo_en.get())+'.jpg'))
        ilosc_pytan_odpowiedzialnych = ilosc_pytan_odpowiedzialnych + 1
        ilosc_pytan.set('Pytanie '+str(ilosc_pytan_odpowiedzialnych)+"/20")
        if ilosc_pytan_odpowiedzialnych == 20:
            messagebox.showinfo(messagebox.showinfo(title='Wygrałeś',message='Ty wygrałeś, twój wynnik jest '+str(score)+'/20'))
            window.destroy()
    else:
        zycia = zycia - 1
        if zycia == 0 or zycia < 0 :
            messagebox.showinfo(title='Przegrałeś',message='Ty przegrałeś, twój wynnik jest '+str(score))
            window.destroy()
        if x == odpA.get():
            btn1.configure(state = DISABLED)
        if x == odpB.get():
            btn2.configure(state = DISABLED)
        if x == odpC.get():
            btn3.configure(state = DISABLED)
        if x == odpD.get():
            btn4.configure(state = DISABLED)
        if x == odpE.get():
            btn5.configure(state = DISABLED)
        if x == odpF.get():
            btn6.configure(state = DISABLED)
        ilosc_zyc.set('Sprób zostało się '+str(zycia))
        windowm = ctk.CTkToplevel()
        my_imagem = ctk.CTkImage(Image.open(folder+"\Images\\"+str(wylosowane_slowo_en.get())+'.jpg'),size = (100,100))
        image_labelm = ctk.CTkLabel(windowm, image=my_imagem, text = "")
        labelm = ctk.CTkLabel(windowm,text = " To jest "+str(wylosowane_slowo_pl.get())+", po angielsku to bedzie "+str(wylosowane_slowo_en.get()))
```
### Sprawdza, czy odpowiedź jest prawidłowa, czy nie.

```
def zmien():
    global odpP, odpA, odpB, odpC, odpD, odpE
    odpP.set(wylosowane_slowo_en.get())
    a = random.randint(1,6)
    if a == 1:
        odpA.set(odpP.get())
        odpB.set(GoogleTranslator(source='pl', target='en').translate(random.choice(listword)))
        odpC.set(GoogleTranslator(source='pl', target='en').translate(random.choice(listword)))
        odpD.set(GoogleTranslator(source='pl', target='en').translate(random.choice(listword)))
        odpE.set(GoogleTranslator(source='pl', target='en').translate(random.choice(listword)))
        odpF.set(GoogleTranslator(source='pl', target='en').translate(random.choice(listword)))
```

### pracuje tak że jest 5 losowych słów i 1 poprawne słowo.

To co wyżej napisano to z Opisu Poziomu trudności Latwy. Obydwa poziomy (Latwy i Średni) są do siebie podobne, jedyną różnicą są odpowiedzi. W latwy 6 dpowiedzi, a w średnim 8 dpowiedzi.


W Poziom średnio-trudnym
```
print(len(wylosowane_slowo))
alpha = len(tluma)
for i in range (0,alpha):
    a = str(tluma[i])
    print (a)
    if a == 'i' or a == 'a' or a == 'e' or a == 'o' or a == 'u':
        tluma2 = tluma2.replace(a,'_')
prompt.set(tluma2)
```
#będzie slowo bez samoglosek.

W poziom trudnym 
Jest tak samo jak w Poziom średnio-trudnym, no poziom trudnym poczebno wpisacz cały wyraz.
Jest Def który będzie sprawdzacz przez Tłumacz Google.




Informacja: 
W każdym poziomie trudności mamy 4 życia.
 Poziom Latwy, Poziom Średni jest do siebie podobne.
 Poziom Średnio-trudny, Poziom trudny jest do siebie podobne.


5. Udizał brali:
Serhii Skyba - Pisał kod.
Artem Kuzniecov - Pisał dokumentację.
Igor Kowalski - Pisał kod.
Vlad Stoliar - Zajmował się bazą danych.
Vlad Prychodko - Zajmował się bazą danych.
Prowodzil test: Serhii Skyba, Igor Kowalski i Artem Kuzniecov.    
