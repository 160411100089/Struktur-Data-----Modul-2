# Struktur-Data---Modul-2
Stack
--------------------------------------------------------------------------------------------------------------------------------
A. Stack

Stack atau tumpukan dapat diartikan sebagai suatu kumpulan data yang seolah-olah terlihat seperti ada data yang diletakkan di atas data yang lain. Kaidah utama dalam konsep stack adalah LIFO yang merupakan singkatan dari Last In First Out, artinya adalah data yang terakhir kali dimasukkan atau disimpan, maka data tersebut adalah yang pertama kali akan diakses atau dikeluarkan. 
Sebuah struktur data dari sebuah stack setidaknya harus mengandung dua buah variabel, misalnya variabel top yang akan berguna sebagai penanda bagian atas tumpukan dan array data dari yang akan menyimpan data-data yang dimasukkan ke dalam stack tersebut.

Operasi-operasi dasar dalam stack:

•	Operasi stack( ), inisialisasi stack yang kosong

•	Operasi push( ), berfungsi untuk memasukkan sebuah nilai atau data ke dalam stack. Sebelum sebuah nilai atau data dimasukkan ke dalamstack, prosedur ini terlebih dahulu akan menaikkan posisi top satu level ke atas. 

•	Operasi pop( ), berfungsi untuk mengeluarkan atau menghapus nilai terakhir (yang berada pada posisi paling atas) dari stack, dengan cara menurunkan nilai top satu level ke bawah.

•	Operasi peek( ), informasi data yang terletak pada posisi top

•	Operasi isEmpty( ), untuk memeriksa apakah stack dalam keadaan kosong

•	Operasi size(), informasi jumlah data yang terdapat pada stack

*fungsi-fungsi yang dibutuhkan untuk mengimplementasikan stacks.

	def stack():
    		s=[]
    		return (s)
	def push(s,data):
    		s.append(data)
	def pop(s):
    		data=s.pop()
    		return(data)
	def peek(s):
    		return(s[len(s)-1])
	def isEmpty(s):
    		return (s==[])
	def size(s):
    		return(len(s))
		
*contoh penggunaan fungsi-fungsi stacks yang telah dibuat

	st=stack()
	isEmpty(st)
	
>>>
Running : True

	push(st,100)
	push(st,23)
	push(st,34)
	pop(st)
	push(st,56)
	pop(st)
	print(st)
	
>>>
Running : [100, 23]

#Ekspressi Aritmatik Infix, Prefix, Postfix

Dalam struktur data terdapat 3 notasi operasi yang dilakukan suatu operasi aritmatika, yaitu prefix, infix dan postfix. Notasi terbentuk dari operand dan operator. Operand adalah data atau nilai yang membantu dalam proses, sedangkan operator adalah fungsi yang digunakan dalam proses. 
Contoh :

A + B * C
2 + 3 * 5

Keterangan : A, B, C, 2, 3, 5 adalah operand. 
+, * adalah operator

- Notasi aritmatika prefix,infix dan postfix:

a. Notasi Prefix,
Notasi Prefix adalah notasi yang operatornya ditempatkan sebelum dua operand.

b. Notasi Infix,
Notasi infix adalah notasi yang operatornya ditempatkan di antara dua operand. Notasi ini telah dikenal secara umum oleh manusia dan selalu digunakan dalam perhitungan aritmatika. 

c. Notasi Postfix,
Notasi postfix adalah notasi yang operatornya ditempatkan setelah dua operand.

*contoh ekspressi aritmatik infix dan konversinya ke prefix dan postfix.

	Infix		Prefix		Postfix
	A+B		+AB		AB+
	(A+B)*C		*+ABC		AB+C*
	(A+B)*(C-D)	*+AB-CD		AB+CD-*
	A+B*C-D		-+A*BCD		ABC*+D-
	A+B-C+D		+-+ABCD		AB+C-D+
	A*B-C*D		-*AB*CD		AB*CD*-

#Evaluasi Ekspressi Postfix

evaluasi untuk ekspressi aritmatika Postfix dilakukan setelah terdapat dua buah operand sebelum sebuah operator. Berikut algoritma untuk mengevaluasi ekspressi aritmatika postfix :

1. baca string mulai dari kiri

2. Jika character yang dibaca adalah sebuah operand, maka push operand tersebut.

3. Jika character yang dibaca adalah sebuah operator, maka pop dua buah operand yang terdapat pada stack, operasikan dua buah operand tersebut dengan operator, dan push hasil operasinya

4. hasil akhir adalah angka terakhir yang terdapat di dalam stack

*code untuk evaluasi ekspressi postfix

	def evaluatePost(postStr):
    		operandStack=stack()
    		operator='+-/*'
    		for i in postStr:
        		if i not in operator:
            			push(operandStack,i)
        		else:
            			oprnd2=pop(operandStack)
            			oprnd1=pop(operandStack)
            			if i=='+':
                			result=float(oprnd1)+float(oprnd2)
            			elif i=='-':
                			result=float(oprnd1)-float(oprnd2)
            			elif i=='*':
                			result=float(oprnd1)*float(oprnd2)
            			else:
                			result=float(oprnd1)/float(oprnd2)
            			push(operandStack,result)
    			return(pop(operandStack))

	print(evaluatePost('45-6*'))

>>>
Running : -6.0

B. Queue

Queue atau antrian merupakan struktur data linear dimana penambahan komponen dilakukan disatu ujung, sementara pengurangan dilakukan diujung lain. Kaidah utama dalam konsep queue adalah FIFO yang merupakan singkatan dari First In First Out, artinya adalah data yang pertama kali dimasukkan atau disimpan, maka data tersebut adalah yang pertama kali akan diakses atau dikeluarkan.
Sebuah queue di dalam program komputer dideklarasikan sebagai sebuah tipe bentukan baru. Sebuah struktur data dari sebuah queue setidaknya harus mengandung dua tiga variabel, yakni variabel head yang akan berguna sebagai penanda bagian depan antrian, variabeltail yang akan berguna sebagai penanda bagian belakang antrian danarray dari yang akan menyimpan data-data yang dimasukkan ke dalam queue tersebut.

Operasi-operasi Queue :

•	Create(), Untuk menciptakan dan menginisialisasi Queue

•	IsEmpty(), Untuk memeriksa apakah Antrian sudah penuh atau belum

•	IsFull(), Untuk mengecek apakah Antrian sudah penuh atau belum

•	Enqueue(), Untuk menambahkan elemen ke dalam Antrian, penambahan elemen selalu ditambahkan di elemen paling belakang

•	Dequeue(), Digunakan untuk menghapus elemen terdepan dari Antrian. Dengan cara menggeser semua elemen antrian kedepan dan mengurangi bagian belakang dengan Penggeseran dilakukan dengan menggunakan looping.

•	Clear(), Untuk menghapus elemen-elemen Antrian

*code-code untuk pembentukan queues dan operasi-operasi yang terdapat pada queues

	def createQueue():
    		q=[]
    		return (q)
	def enqueue(q,data):
    		q.insert(0,data)
    		return(q)
	def dequeue(q):
    		data=q.pop()
    		return(data)
	def isEmpty(q):
    		return (q==[])
	def size(q):
    		return (len(q))

C. Deques

DeQue, dikenal sebagai antrian berujung dua (double-ended), adalah suatu koleksi item terurut serupa dengan queue. Perbedaannya? Sifat tidak terikat untuk penambahan dan penghapusan item-item dari antrian. Item baru dapat ditambahkan ke depan atau belakang. Karena itu, item yang ada dapat dihapuskan dari salah satu ujung.

Operasi-operasi Deques :

•	deque(), membuat suatu deque baru yang kosong. Tidak perlu parameter dan mengembalikan suatu deque kosong.

•	addFront(item), menambahkan suatu item baru ke depan dari deque. Perlu item dan tidak mengembalikan apapun.

•	addRear(item), menambahkan suatu item baru ke ekor dari deque. Perlu item dan tidak mengembalikan sesuatu.

•	removeFront(), menghapus item depan dari deque. Tidak perlu parameter dan mengembalikan item. Deque termodifikasi.

•	removeRear(), menghapus item ujung (ekor) dari deque. Tidak perlu parameter dan mengembalikan item. Deque berubah.

•	isEmpty(), menguji apakah deque dalam kondisi kosong. Tidak perlu parameter dan mengembalikan suatu nilai boolean.

•	size(), mengembalikan jumlah item dalam deque. Tidak perlu parameter dan mengembalikan suatu integer.


Praktikum Struktur Data – 2019
#Modul 2 – Stack
-----------------------------------------------------------------------------------------

Buatlah suatu modul dengan nama stack, dengan fungsi-fungsi utama yang terdapat dalam modul adalah:

- stack( )	: inisialisasi stack kosong

- push(data)	: push suatu data ke dalam stack

- pop ( )	: penghapusan data yang berada pada top of the stack. Return value berupa data yang dihapus dari stack tersebut
	
- peep ( )	: informasi yang terdapat pada top of the stack

- isEmpty( )	: memeriksa stack apakah dalam keadaan kosong

- size( )	: informasi jumlah data yang terdapat pada stack

Buatlah modul dengan nama stackImplementation, yang berisi fungsi-fungsi untuk implementasi-implementasi penggunaan konsep stack, antara lain :

1.	reverseWord (kata)	:

Gunakan fungsi-fungsi yang terdapat pada modul stack untuk membalik suatu kata. Output dari fungsi reverseWord(kata) ini adalah kata yang sudah disusun secara terbalik, seperti berikut

	stack.reverseWord('kita')
	
	>>>
	Running : 'atik'
	
2.	decToBin(num) :

Gunakan fungsi-fungsi yang terdapat pada modul stack untuk mengkonversi suatu bilangan decimal menjadi bilangan biner, seperti contoh berikut :

	stack.decToBin(12)
	
	>>>
	Running : '1100'
	
3. evaluatePost(str):

Gunakan fungsi-fungsi yang terdapat pada modul stack untuk mengevaluasi ekspressi matematika postfix, dengan return value berupa hasil operasi matematika, dengan ketentuan sebagai berikut :

a. antara operand maupun operator, dipisahkan dengan spasi, misalkan : 8 17 + yang berarti 8 + 17

b. Tambahkan pengecekan error, antara lain :

i. Jika jumlah operand terlalu banyak

ii. Jika jumlah operand terlalu sedikit

iii. Jika terdapat operasi pembagian dengan nol, seperti 9 0 /, yang berarti 9:0

Berikut adalah contoh penggunaan fungsi evaluatePost(str):

	a = '6 0 81'
	evaluatePost(a)
	
	>>>
	Running: Error : Terlalu Banyak Operand
	
	a = '8 7 + 0/'
	evaluatePost(a)
	
	>>>
	Running: Error : Pembagian dengan Nol
	
	a = '21 2 + * /'
	evaluate Post(a)
	
	>>>
	Running: Error : Operand terlalu sedikit
	
	a = '10 11 1 + - 5 *'
	evaluatePost(a)
	
	>>>
	Running: -10.0
	
4.	parenthesesCheck(str):

Gunakan fungsi-fungsi yang terdapat pada modul stack untuk pengecekan kurung pada ekspressi matematika, dengan return value berupa nilai True jika ekspressi matematika sudah benar, dan false jika masih terdapat kesalahan. Selain nilai True dan False, tambahkan pesan error jika terjadi kesalahan, antara lain :

o Jumlah kurung buka terlalu banyak 

o Jumlah kurung tutup terlalu banyak

o  Kurung buka dan kurung tutup tidaklah cocok


*Contoh penggunaan fungsi dan output yang dihasilkan, dapat dilihat pada contoh berikut

	parenthesesCheck('{(3 + 5)*(9 - 2)}')
	>>>
	Running : (true, 'Tidak ada Error')
	
	parenthesesCheck('21/(56 + 2)')
	>>>
	Running : (False, 'Jumlah Kurung Buka Lebih Banyak')
	
	parenthesesCheck('(4 -5)/12 + 7')
	>>>
	Running : (False, 'Jumlah Kurung Tutup Lebih Banyak')
	
	parenthesesCheck('67*(5 + 2)/(12 - 6'))
	>>>
	Running : (False, 'Kurung Buka dan Kurung Tutup tidak Cocok')
	
Jawaban Praktikum
------------------------------------------------------------------------------------------------

#Nomer 1

	def stack():
    		s=[]
    		return(s)

	def push(s,data):
    		s.append(data)
    
	def pop(s):
    		data=s.pop()
    		return(data)

	def peek(s):
    		return(s[len(s)-1])

	def IsEmpty(s):
    		return(s==[])

	def size(s):
    		return(len(s))

	def ReverseWord(data):
    		s=stack()
    		for i in range(len(data)):
        		push(s,data[i])
    		hasil=' '
    		while not IsEmpty(s):
        		hasil+=s.pop()
    		return (hasil)
	print(ReverseWord('Ahadi'))

#Nomer 2

	def stack():
    		s=[]
    		return(s)

	def push(s,data):
    		s.append(data)
    
	def pop(s):
    		data=s.pop()
    		return(data)

	def peek(s):
    		return(s[len(s)-1])

	def IsEmpty(s):
    		return(s==[])

	def size(s):
    		return(len(s))

	def Biner(angka):
    		s = stack()
    		while angka > 0:
        		biner = int(angka%2)
        		push(s,biner)
        		angka = (angka - biner) / 2
        
    		hasilBenar = " "

    		for i in range(len(s)):
        		hasilBenar += (str(pop(s)))
    		print("Hasil Biner:",end=" ")
    		return (hasilBenar)

	print(Biner(8))

#Nomer 3
	
	\\\Modul Stack
	def stack():
    		st=[]
    	return (st)
		def push(st,data):
    		st.append(data)
	def pop(st):
    		data=st.pop()
    		return(data)
	def peek(st):
    		return(st[len(st)-1])
	def isEmpty(st):
    		return (st==[])
	def size(st):
    		return(len(st))

	\\\Evaluation Post Program
	import Stack

	def evaluatePost(string):
    		s=Stack()
    		hasil = 0
    		for i in string:
        		if i == '+':
            			if (s.size(s)>2):
                			if (s.peek(s)==' '):
                    				s.pop(s)
                			akhir=(Stack.pop(s))
                			if s.peek(s)==' ':
                    				s.pop(s)
                			hasil=s.pop(s)+akhir
                			s.push(s,hasil)
            			else:
                			return 'Error: operand terlalu sedikit'
        		elif i == '-':
            			if (s.size(s)>2):
                			if (s.peek(s)==' '):
                    				s.pop(s)
                			akhir=(s.pop(s))
                			if s.peek(s)==' ':
                    				s.pop(s)
                			hasil=s.pop(s)-akhir
                			s.push(s,hasil)
            			else:
                			return 'Error: operand terlalu sedikit'
        		elif i == '*':
            			if (s.size(s)>2):
                			if (s.peek(s)==' '):
                    				s.pop(s)
                			akhir=(s.pop(s))
                			if s.peek(s)==' ':
                    				s.pop(s)
                			hasil=akhir*s.pop(s)
                			s.push(s,hasil)
            			else:
                			return 'Error: operand terlalu sedikit'
        		elif i == '/':
            			if (s.size(s)>2):
                			if (s.peek(s)==' '):
                    				s.pop(s)
                			akhir=(s.pop(s))
                			if s.peek(s)==0:
                    				return 'Error : Pembagian dengan nol'
                			akhir=(s.pop(s))
                			if s.peek(s)==' ':
                    				s.pop(s)
                			hasil=s.pop(s)/akhir
                			s.push(s,hasil)
            			else:
                			return 'Error: operand terlalu sedikit'
        		elif i==' ':
            			s.push(s,i)
        		else:
            			if not(s.isEmpty(s)):
                			if (s.peek(s)!=' '):
                    				jumlah=(s.pop(s)*10) + int(i)
                    				s.push(s,jumlah)
                			else:
                    				s.push(s,int(i))
            			else:
                			s.push(s,int(i))
    		if s.size(s)>1:
        		return 'Error: operand terlalu sedikit'
    		else:
        		return s.pop(s)
			
#Nomer 4

	def stack():
    		s=[]
    		return(s)

	def push(s,data):
    		s.append(data)
    
	def pop(s):
    		data=s.pop()
    		return(data)

	def peek(s):
    		return(s[len(s)-1])

	def isEmpty(s):
    		return (s==[])
    
	def size(s):
    		return (len(s))
	def parenthesCheck(teks):
    		s=stack()
    		cek = True
    		eror = 'tidak ada eror'
    		for i in (teks):
        		if i == "(" or i =="{" :
            			push(cek, i)
        		elif (i ==")") and (not(isEmpty(s))) and (peep(s)=="("):
            			pop(s)
        		elif ((i ==")") or (i =="}")) and (isEmpty(s)):
            			eror = ("kelebihan kuring tutup")
        		elif (i=="}") and not (isEmpty(s)) and (peep(s)=="{") :
            			pop(s)
        		elif ((i == ")") and (peep(s)=="{")) or (i=="}" and (peep(s)=="(")):
            			eror = ("kurung buka dan kurung tutup tidak sesuai")
            			pop(s)
    		if not (isEmpty(s)):
        		eror="kelebihan kurung buka"
        		cek = False
    		elif eror != "tidak ada eror" and isEmpty(s):
        		cek = False
    		return cek, eror
	parenthesCheck("{ (3+4)*(9-2)}")
