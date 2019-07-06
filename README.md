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
	
Running : True

	push(st,100)
	push(st,23)
	push(st,34)
	pop(st)
	push(st,56)
	pop(st)
	print(st)
	
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
Modul 2 – Stack
------------------------------------------------------------------------------------------------------
