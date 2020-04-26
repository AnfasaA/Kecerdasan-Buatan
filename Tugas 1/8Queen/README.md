## 8Queen
Kode untuk penyelesaian 8 Queen  dapat dilihat dengan menekan tombol biru disebelah [8Queen](https://github.com/AnfasaA/Kecerdasan-Buatan/blob/master/Tugas%201/8Queen/8Queen.cpp).

Dalam kode diatas terdapat beberapa fungsi sebagai berikut :

    bool solveNQUtil(int board[N][N], int col) 
    { 
        if (col >= N) 
            return true; 
        for (int i = 0; i < N; i++) {
            if ((ld[i - col + N - 1] != 1 && 
                      rd[i + col] != 1) && cl[i] != 1) { 
                board[i][col] = 1; 
                ld[i - col + N - 1] = 
                              rd[i + col] = cl[i] = 1; 
                if (solveNQUtil(board, col + 1)) 
                    return true; 
                board[i][col] = 0; // BACKTRACK 
                ld[i - col + N - 1] = 
                             rd[i + col] = cl[i] = 0; 
            } 
        } 
        return false; 
    } 
Fungsi diatas merupakan sebuah fungsi berulang untuk menyelesaikan 8Queen problem dan akan return false jika ratu tidak bisa ditempatkan di row mana saja.

        bool solveNQ() { 
        int board[N][N] = { { 0, 0, 0, 0, 0, 0, 0, 0 }, 
                            { 0, 0, 0, 0, 0, 0, 0, 0 }, 
                            { 0, 0, 0, 0, 0, 0, 0, 0 }, 
                            { 0, 0, 0, 0, 0, 0, 0, 0 } }; 
      
        if (solveNQUtil(board, 0) == false) { 
            printf("Solution does not exist"); 
            return false; 
        } 
      
        printSolution(board); 
        return true; 
	    } 
Fungsi diatas berfungsi untuk menyelesaikan masalah 8 Queen dengan backtracking, yang akan mereturn false jika queen tidak dapat diletakkan, dan return true dan menampilkan peletakan dari queen.


