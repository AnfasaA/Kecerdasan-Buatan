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
kode untuk penyelesaian 8Puzzle dengan menggunakan DFS atau Depth First Search dapat dilihat dengan menekan tombol biru disebelah [8PuzzleDFS](https://github.com/AnfasaA/Kecerdasan-Buatan/blob/master/Tugas%201/8Puzzle/DFS/8puzzle_DFS.cpp).
