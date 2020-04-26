## 8Queen (Hill Climbing)

kode untuk penyelesaian 8Queen dengan menggunakan Hill Climbing dapat dilihat dengan menekan tombol biru disebelah [8QueenHillClimbing](https://github.com/AnfasaA/Kecerdasan-Buatan/blob/master/Tugas%202/8Queen/8Queen_HillClimbing.cpp).

Hill Climbing adalah pencarian heuristik yang digunakan untuk masalah optimasi matematis di bidang Inteligensi Buatan. Dengan sejumlah besar input dan fungsi heuristik yang baik, ia mencoba untuk menemukan solusi yang cukup baik untuk masalah tersebut. Solusi ini mungkin bukan global optimal maksimum.

**Jenis Hill Climbing**

 1. Steepest-Ascent Hill Climbing
     Pertama-tama memeriksa semua node tetangga dan kemudian memilih simpul yang paling dekat dengan keadaan solusi pada simpul berikutnya.

	-   Evaluasi keadaan awal. Jika status tujuan maka keluar dari yang lain jadikan status saat ini sebagai keadaan awal
	-   Ulangi langkah ini sampai solusi ditemukan atau keadaan saat ini tidak berubah
	-   Exit
 2. Simple Hill Climbing
     Ini memeriksa node tetangga satu per satu dan memilih node tetangga pertama yang mengoptimalkan biaya saat ini sebagai node berikutnya. Ini memeriksa node tetangga satu per satu dan memilih node tetangga pertama yang mengoptimalkan biaya saat ini sebagai node berikutnya.
     

 3. Stochastic Hill Climbing
     Itu tidak memeriksa semua node tetangga sebelum memutuskan node mana yang akan dipilih. Itu hanya memilih node tetangga secara acak dan memutuskan (berdasarkan jumlah peningkatan tetangga itu) apakah akan pindah ke tetangga itu atau untuk memeriksa yang lain.

dalam kode diatas, ada beberapa fungsi yang akan dijelaskan dibawah ini.

    int is_attack(int i,int j) {
        int k,l;
        for(k=0;k<N;k++) {
            if((board[i][k] == 1) || (board[k][j] == 1))
                return 1;
        }
        for(k=0;k<N;k++) {
            for(l=0;l<N;l++) {
                if(((k+l) == (i+j)) || ((k-l) == (i-j))) {
                    if(board[k][l] == 1)
                        return 1;
                }
            }
        }
        return 0;
    }
Fungsi diatas merupakan fungsi yang digunakan untuk mengecek apakah sebuah queen bisa diserang oleh queen lain.

    int N_queen(int n) {
        int i,j;
        if(n==0)
            return 1;
        for(i=0;i<N;i++) {
            for(j=0;j<N;j++) {
                if((!is_attack(i,j)) && (board[i][j]!=1)) {
                    board[i][j] = 1;
                    if(N_queen(n-1)==1) {
                        return 1;
                    }
                    board[i][j] = 0;
                }
            }
        }
        return 0;
    }    
Fungsi diatas digunakan untuk meletakkan queen yang dirasa aman ketika tidak ada queen yang menyerang.


