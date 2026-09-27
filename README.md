# Modular-Tuple-Graphs-Cycles-and-Structural-Candidates-2N49R1M3-Project-
The 2N49R1M3 project investigates composite candidate structures and semiprimes N = p * q (with p, q > 5) via two complementary modular models. 

Multiplicative Candidate Construction:
N = a * 2^b + c' * 3^d
where N in U_30 (residues 1, 7, 11, 13, 17, 19, 23, 29 mod 30). We analyze p-adic valuations (v_2, v_3) on decimal suffixes to isolate modular anchors in 6k +/- 1.

Quad-Value Position Mapping:
Mapping N +/- (q +/- p) yields symmetric ordered positions w < x < y < z around N (w + z = 2N, x + y = 2N).
​Residues mod 6: Governed strictly by N mod 6. For N = 5 mod 6, w = z = 5 mod 6 and x, y in {1, 3} mod 6.
​Deterministic Slots mod 5: In 78% of modulo pairs [(p mod 5, q mod 5)], exactly one slot in {w, x, y, z} is divisible by 5 (e.g., (2,2) -> w = 0 mod 5; (2,3) -> x = 0 mod 5).

Graph Mapping & Cycle Detection
​By iterating the transition N -> {w, x, y, z} and keeping only semiprime vertices with factors > 5, we construct a directed graph.
​For N <= 50000, empirical analysis reveals:
​10 trivial length-2 mirror cycles (e.g., z(119) = 143 and w(143) = 119, producing 119 <-> 143).
​13 genuine cycles of length k >= 3.
​Representative Cycles:
​Length 3:
671 --(y)--> 721 --(w)--> 611 --(z)--> 671
10249 -> 10489 -> 11089 -> 10249
14257 -> 14579 -> 14279
16379 -> 17879 -> 16957
​Length 5:
4559 --(y)--> 4609 --(y)--> 5017 --(x)--> 4873 --(z)--> 5327 --(w)--> 4559

