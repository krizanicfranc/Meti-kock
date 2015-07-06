# Meti-kock
from tkinter import *
import random

import csv

class Kocke():
    def __init__(self, master):

        self.kocka1=0
        self.kocka2=0
        self.kocka3=0
        self.kocka4=0
        self.kocka5=0
        self.vsota=0

        self.v14=0
        self.v16=0
        self.v18=0
        self.v110=0
        self.v112=0
        self.v120=0
        
        self.v24=0
        self.v26=0
        self.v28=0
        self.v210=0
        self.v212=0
        self.v220=0

        self.v34=0
        self.v36=0
        self.v38=0
        self.v310=0
        self.v312=0
        self.v320=0

        self.v44=0
        self.v46=0
        self.v48=0
        self.v410=0
        self.v412=0
        self.v420=0

        self.v54=0
        self.v56=0
        self.v58=0
        self.v510=0
        self.v512=0
        self.v520=0

        self.trenutni_r=0
        
       
        

        Label(master, text="Število kock:").grid(row=0, column=0)

        st_kock = IntVar(master)
        st_kock.set(1)

        izb_kock = [1, 2, 3, 4, 5]
        kocke = OptionMenu(master, st_kock, *izb_kock) #stevilo kock
        kocke.grid(row = 0, column = 1)

        Label(master, text="Število strani:").grid(row=1, column=0)

        st_strani = IntVar(master)
        st_strani.set(6)

        izb_strani = [4, 6, 8, 10, 12, 20]
        strani = OptionMenu(master, st_strani, *izb_strani)
        strani.grid(row = 1, column = 1)

        self.st_strani = st_strani
        self.st_kock = st_kock

        Label(master, text="Izid:").grid(row = 1, column = 2)

        Label(master, text="1. kocka").grid(row = 0, column = 3)
        Label(master, text="2. kocka").grid(row = 0, column = 4)
        Label(master, text="3. kocka").grid(row = 0, column = 5)
        Label(master, text="4. kocka").grid(row = 0, column = 6)
        Label(master, text="5. kocka").grid(row = 0, column = 7)

        self.rez_kocka1 = IntVar(value = self.kocka1)
        rez_kocka1 = Label(master, textvariable = self.rez_kocka1)
        rez_kocka1.grid(row = 1, column = 3)
        
        self.rez_kocka2 = IntVar(value = self.kocka2)
        rez_kocka2 = Label(master, textvariable = self.rez_kocka2)
        rez_kocka2.grid(row = 1, column = 4)

        self.rez_kocka3 = IntVar(value = self.kocka3)
        rez_kocka3 = Label(master, textvariable = self.rez_kocka3)
        rez_kocka3.grid(row = 1, column = 5)

        self.rez_kocka4 = IntVar(value = self.kocka4)
        rez_kocka4 = Label(master, textvariable = self.rez_kocka4)
        rez_kocka4.grid(row = 1, column = 6)

        self.rez_kocka5 = IntVar(value = self.kocka5)
        rez_kocka5 = Label(master, textvariable = self.rez_kocka5)
        rez_kocka5.grid(row = 1, column = 7)

        def vrzi_kocke_prosim(a=st_strani.get(),b=st_kock.get()):
            self.kocka1 = random.randint(1, st_strani.get())
            self.rez_kocka1.set(self.kocka1)
            if st_kock.get() > 1:
                self.kocka2 = random.randint(1, st_strani.get())
                self.rez_kocka2.set(self.kocka2)
            else:
                self.rez_kocka2.set(0)
                self.kocka2 = 0

            if st_kock.get() > 2:
                self.kocka3 = random.randint(1, st_strani.get())
                self.rez_kocka3.set(self.kocka3)
            else:
                self.rez_kocka3.set(0)
                self.kocka3 = 0

            if st_kock.get() > 3:
                self.kocka4 = random.randint(1, st_strani.get())
                self.rez_kocka4.set(self.kocka4)
            else:
                self.rez_kocka4.set(0)
                self.kocka4 = 0

            if st_kock.get() > 4:
                self.kocka5 = random.randint(1, st_strani.get())
                self.rez_kocka5.set(self.kocka5)
            else:
                self.rez_kocka5.set(0)
                self.kocka5 = 0



        def pocisti():
            self.rez_kocka1.set(0)
            self.rez_kocka2.set(0)
            self.rez_kocka3.set(0)
            self.rez_kocka4.set(0)
            self.rez_kocka5.set(0)



        def pisi():
            with open('rekordi.csv', 'w') as csvfile:
                writer = csv.writer(csvfile)
                writer.writerow(('N',4,6,8,10,12,20))

                writer.writerow((1,self.v14,self.v16,self.v18,self.v110,self.v112,self.v120))
                writer.writerow((2,self.v24,self.v26,self.v28,self.v210,self.v212,self.v220))
                writer.writerow((3,self.v34,self.v36,self.v38,self.v310,self.v312,self.v320))
                writer.writerow((4,self.v44,self.v46,self.v48,self.v410,self.v412,self.v420))
                writer.writerow((5,self.v54,self.v56,self.v58,self.v510,self.v512,self.v520))

        def beri(v,s):
            with open('rekordi.csv', encoding='utf8') as csvf:
                      bralec = csv.reader(csvf)
                      i=0
                      j=0
                      for row in bralec:
                          if i%2 == 0:
                              j+=1
                              if j == v+1:
                                  return int(row[s])
                                  
                          elif i%2 == 1:
                              pass
                          i+=1
                      
                      
                    
                          
        def isci_rekorde_prosim():
            if st_kock.get() == 1:
                if st_strani.get() == 4:
                    if self.vsota > self.v14:
                        self.v14 = self.vsota
                elif st_strani.get() == 6:
                    if self.vsota > self.v16:
                        self.v16 = self.vsota
                elif st_strani.get() == 8:
                    if self.vsota > self.v18:
                        self.v18 = self.vsota
                elif st_strani.get() == 10:
                    if self.vsota > self.v110:
                        self.v110 = self.vsota
                elif st_strani.get() == 12:
                    if self.vsota > self.v112:
                        self.v112 = self.vsota
                elif st_strani.get() == 20:
                    if self.vsota > self.v120:
                        self.v120 = self.vsota

            if st_kock.get() == 2:
                if st_strani.get() == 4:
                    if self.vsota > self.v24:
                        self.v24 = self.vsota
                elif st_strani.get() == 6:
                    if self.vsota > self.v26:
                        self.v26 = self.vsota
                elif st_strani.get() == 8:
                    if self.vsota > self.v28:
                        self.v28 = self.vsota
                elif st_strani.get() == 10:
                    if self.vsota > self.v210:
                        self.v210 = self.vsota
                if st_strani.get() == 12:
                    if self.vsota > self.v212:
                        self.v212 = self.vsota
                if st_strani.get() == 20:
                    if self.vsota > self.v220:
                        self.v220 = self.vsota

            if st_kock.get() == 3:
                if st_strani.get() == 4:
                    if self.vsota > self.v34:
                        self.v34 = self.vsota
                elif st_strani.get() == 6:
                    if self.vsota > self.v36:
                        self.v36 = self.vsota
                elif st_strani.get() == 8:
                   if self.vsota > self.v38:
                        self.v38 = self.vsota
                elif st_strani.get() == 10:
                    if self.vsota > self.v310:
                        self.v310 = self.vsota
                elif st_strani.get() == 12:
                    if self.vsota > self.v312:
                        self.v312 = self.vsota
                elif st_strani.get() == 20:
                    if self.vsota > self.v320:
                        self.v320 = self.vsota

            if st_kock.get() == 4:
                if st_strani.get() == 4:
                    if self.vsota > self.v44:
                        self.v44 = self.vsota
                elif st_strani.get() == 6:
                    if self.vsota > self.v46:
                        self.v46 = self.vsota
                elif st_strani.get() == 8:
                   if self.vsota > self.v48:
                        self.v48 = self.vsota
                elif st_strani.get() == 10:
                    if self.vsota > self.v410:
                        self.v410 = self.vsota
                elif st_strani.get() == 12:
                    if self.vsota > self.v412:
                        self.v412 = self.vsota
                elif st_strani.get() == 20:
                    if self.vsota > self.v420:
                        self.v420 = self.vsota

            if st_kock.get() == 5:
                if st_strani.get() == 4:
                    if self.vsota > self.v54:
                        self.v54 = self.vsota
                elif st_strani.get() == 6:
                    if self.vsota > self.v56:
                        self.v56 = self.vsota
                elif st_strani.get() == 8:
                    if self.vsota > self.v58:
                        self.v58 = self.vsota
                elif st_strani.get() == 10:
                    if self.vsota > self.v510:
                        self.v510 = self.vsota
                elif st_strani.get() == 12:
                    if self.vsota > self.v512:
                        self.v512 = self.vsota
                elif st_strani.get() == 20:
                        if self.vsota > self.v520:
                            self.v520 = self.vsota
        #trenutni rekord
        def izpisi_rekord_prosim():
            
            if st_strani.get()==4:
                s = 1
            elif st_strani.get()==6:
                s = 2
            elif st_strani.get()==8:
                s = 3
            elif st_strani.get()==10:
                s = 4
            elif st_strani.get()==12:
                s = 5
            elif st_strani.get()==20:
                s = 6
            v = st_kock.get()
            self.trenutni_r = beri(v,s)
            self.trenutni_max.set(self.trenutni_r)
            return self.trenutni_max.set(self.trenutni_r)

        def sestej_mete():
            self.vsota = (self.kocka1 + self.kocka2 +
                          self.kocka3+ self.kocka4 +
                          self.kocka5)
            self.rez_vsota.set(self.vsota)    




        def vrzi():
            pocisti()    

            vrzi_kocke_prosim()
            
            sestej_mete()

            
            isci_rekorde_prosim()
            
            pisi()

            izpisi_rekord_prosim()


            
        gumb_vrzi = Button(master, text="Vrzi!", command= vrzi)
        gumb_vrzi.grid(row = 2, column = 0)


        Label(master, text="Vsota metov:").grid(row = 2, column = 2, columnspan = 2)
        
        self.rez_vsota = IntVar(value = self.vsota)
        rez_vsota = Label(master, textvariable=self.rez_vsota)
        rez_vsota.grid(row = 2, column = 4)

        Label(master, text="Trenutni rekord:").grid(row = 2, column =5, columnspan = 2)

        self.trenutni_max = IntVar(value = self.trenutni_r)
        trenutni_max = Label(master, textvariable = self.trenutni_max)
        trenutni_max.grid(row = 2, column = 7)


            
   

root = Tk()

aplikacija = Kocke(root)

root.mainloop()

