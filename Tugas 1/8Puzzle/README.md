
## 8Puzzle

## BFS

kode untuk penyelesaian 8Puzzle dengan menggunakan BFS atau Breadth First Search dapat dilihat dengan menekan tombol biru disebelah [8PuzzleBFS](https://github.com/AnfasaA/Kecerdasan-Buatan/blob/master/Tugas%201/8Puzzle/BFS/8puzzle_BFS.cpp).

Breadth First Search merupakan pencarian node tujuan dengan pencarian secara melebar, pertama kita mengunjungi node pertama lalu mengunjungi node yang bertetangga terlebih dahulu. Lalu mengunjungi node yang bertetangga dengan node yang telah dikunjungi.

Contoh BFS :

![](https://i2.wp.com/algorithms.tutorialhorizon.com/files/2015/05/Tree-Traversals-BFS-e1514854406978.png)

Dalam kode diatas, kode yang menampilkan fungsi BFS terdapat dalam fungsi dibawah :

    int bfs(){
		deque<Node> toexpand;
		deque<State> expanded;
		
		toexpand.push_back(*this);
		while ( !toexpand.empty() ){
			if ( toexpand.front().s.goal()==1 ){ 
				cout << "------|BFS|------" << endl;
				cout << "Solution found!" << endl;
				toexpand.front().print();
				cost = toexpand.front().cost;
				toexpand.clear();
				return cost;
			}
			else{
				if ( !(toexpand.front().expanded(&expanded)) ){
					toexpand.front().expand(&toexpand);
					expanded.push_front( toexpand.front().s );
					toexpand[1].cost=toexpand[0].cost+1;
				}
				toexpand.pop_front();
			}
		}
		if ( toexpand.empty() ) cout << endl << "Solution NOT found!" << endl;
		return 0;
	}
Pencarian akan dilakukan dengan memperluas jangkauan, pencarian dimulai dari node teratas lalu dilanjutkan ke node sebelahnya bukan ke node yang berada dibawahnya.

    int expanded(deque<State> *deque){
		int max=(*deque).size()>depth?depth:(*deque).size();
		for (int i=0; i<max; i++){
			if ( s.equal( (*deque)[i] ) ){
				return 1;
			}
		}
		return 0;
	}

## DFS
kode untuk penyelesaian 8Puzzle dengan menggunakan DFS atau Depth First Search dapat dilihat dengan menekan tombol biru disebelah [8PuzzleDFS](https://github.com/AnfasaA/Kecerdasan-Buatan/blob/master/Tugas%201/8Puzzle/DFS/8Puzzle_DFS.cpp).

Depth First Search merupakan algoritma penelusuran pada struktur pohon berdasarkan kedalaman terlebih dahulu, simpul ditelusuri dari root kemudian ke salah satu simpul anaknya(biasanya prioritas ke kiri), lalu dari simpul tersebut akan dicari terus sampai pada simpul ujung yang tidak mempunyai anak lagi. setelah penelusuran sampai ke paling bawah, maka penelusuran akan kembali ke 1 level diatasnya dan mencari anak lainnya yang belum di telusuri.

Contoh DFS :

![enter image description here](http://www.crazyforcode.com/wp-content/uploads/2016/04/DFS.png)

Dalam kode diatas, kode yang menampilkan fungsi BFS terdapat dalam fungsi dibawah :

    int dfs(int idsdepth){
		deque<Node> toexpand;
		
		if (idsdepth==-1) idsdepth = sizeof(int);
		
		toexpand.push_back(*this);
		while ( !toexpand.empty() ){
				if (toexpand.back().depth < idsdepth){
					if ( toexpand.back().s.goal()==1 ){ 
						if (idsdepth == sizeof(int)) 
							cout << "------|DFS|------" << endl;
						cout << "Solution found!" << endl;
						toexpand.back().print();
						toexpand.clear();
						return cost;
					}
					else{
						Node t;
						t= toexpand.back().copy();
						toexpand.pop_back();
						t.expand(&toexpand);
					}
				}
				else return 0;
		}
		if ( toexpand.empty() ) cout << endl << "Solution NOT found!" << endl;
		return 0;
	}
Algoritma DFS adalah algoritma rekursif yang menggunakan gagasan backtracking. Ini melibatkan pencarian lengkap dari semua node dengan melanjutkan, jika mungkin, dengan mundur.

## IDS
kode untuk penyelesaian 8Puzzle dengan menggunakan IDS atau Iterative Deepening Search dapat dilihat dengan menekan tombol biru disebelah [8PuzzleIDS](https://github.com/AnfasaA/Kecerdasan-Buatan/blob/master/Tugas%201/8Puzzle/IDS/8Puzzle_IDS.cpp).

Iterative Deepening Search merupakan pengembangan dari algoritma Depth First Search, IDS menggunakan konsep penelusuran secara DFS dimulai dari limit 1. Saat solusi belum ditemukan makan pencarian dilakukan lah iterasi ke-2, pencarian kini limitnya bertambah menjadi 1 level menjadi limit 2, bila solusi masih belum ditemukan lakukan kembali iterasi ke-3 dengan menambah limit 1 level menjadi limit 3. Begitu seterusnya hingga ditemukan solusi yang dicari.

Contoh IDS :

![enter image description here](https://media.geeksforgeeks.org/wp-content/cdn-uploads/iddfs3.png)

Dalam kode diatas, kode yang menampilkan fungsi IDS terdapat dalam fungsi dibawah :

    int dfs(int idsdepth){
		deque<Node> toexpand;
		
		if (idsdepth==-1) idsdepth = sizeof(int);
		
		toexpand.push_back(*this);
		while ( !toexpand.empty() ){
				if (toexpand.back().depth < idsdepth){
					if ( toexpand.back().s.goal()==1 ){ 
						if (idsdepth != sizeof(int))  
							cout << "------|IDS|------" << endl;
						cout << "Solution found!" << endl;
						toexpand.back().print();
						toexpand.clear();
						return cost;
					}
					else{
						Node t;
						t= toexpand.back().copy();
						toexpand.pop_back();
						t.expand(&toexpand);
					}
				}
				else return 0;
		}
		if ( toexpand.empty() ) cout << endl << "Solution NOT found!" << endl;
		return 0;
	}
	
	int ids(){
		for(int i=0;;i++){
			int t = dfs(i);
			if (t!=0) return t; 
		}
	}
	
Iterative Deepening Search merupakan sebuah strategi umum yang biasanya dikombinasikan dengan Depth First tree search, yang akan menemukan berapa depth limit terbaik untuk digunakan. Hal ini dilakukan dengan secara menambah limit secara bertahap, mulai dari 0,1, 2, dan seterusnya sampai goal sudah ditemukan.


