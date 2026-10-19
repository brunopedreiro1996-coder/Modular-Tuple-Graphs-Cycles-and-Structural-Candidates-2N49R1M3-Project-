# Conjectura dos Cortes

**Semiprimos p·q com p crescente, a partir de w = 4^n + 2^s − 1**

**Autor da formulação:** Bruno Paiva Viana (pesquisador independente). **Verificação computacional e redação:** com assistência do Claude (Anthropic). **Data:** 18 de outubro de 2026.

**Status:** conjectura apoiada em evidência numérica. Não há demonstração. Não verifiquei sistematicamente se ela já aparece na literatura. Críticas, contraexemplos e referências são muito bem-vindos.

## Resumo

Para cada n ≥ 3, procuramos semiprimos N = p·q cujo valor w = N − (p+q) seja igual a 4^n + 2^s − 1, onde p − 1 e q − 1 são montados a partir de uma fatoração algébrica de 2^t + 1. Com isso p e q são explícitos, não é preciso fatorar nada, e **p cresce junto com n**. A conjectura afirma que, para todo n ≥ 3, existe ao menos um par (p, q) de primos desse tipo. Em testes de n = 3 até n = 200 nenhum n ficou sem exemplo, e a quantidade de exemplos por n cresce com n.

## 1. Notação e identidade básica

Sejam p < q primos ímpares, N = p·q e w(N) = N − (p+q). Então

```
w(N) + 1 = (p − 1)(q − 1).
```

Portanto, dar w equivale a dar o produto (p−1)(q−1) = w + 1.

## 2. Fatoração algébrica de 2^t + 1

Se t = u·r com r ímpar e r ≥ 3, então

```
2^t + 1 = (2^u + 1) · B,   com   B = (2^t + 1)/(2^u + 1) = 2^(u(r−1)) − 2^(u(r−2)) + ... + 1.
```

B é inteiro ímpar e B ≥ 3. Exemplo: t = 9, u = 3, r = 3 dá 2^9 + 1 = 513 = 9 · 57.

## 3. Definições

Fixe n ≥ 3. Um **corte** é uma escolha de inteiros (s, r, a, b) com:

- 1 ≤ s ≤ 2n − 1 e t = 2n − s;
- r ímpar, r ≥ 3, r divide t, e u = t/r;
- a, b ≥ 1 com a + b = s.

Ponha A = 2^u + 1, B = (2^t + 1)/A, e

```
P = 2^a · A + 1,    Q = 2^b · B + 1.
```

O corte é **bom** se P e Q são primos e distintos. (Como A, B ≥ 3, tem-se P, Q ≥ 7.) Seja G(n) o número de pares não ordenados {P, Q} obtidos de cortes bons.

**Proposição (identidade exata).** Se P e Q vêm de um corte, então

```
P·Q − P − Q = 4^n + 2^s − 1.
```

*Prova.* (P−1)(Q−1) = 2^(a+b) · A · B = 2^s (2^t + 1) = 2^(s+t) + 2^s = 4^n + 2^s. Subtraia 1. ∎

Logo, se o corte é bom, N = P·Q é um semiprimo com w(N) = 4^n + 2^s − 1.

## 4. Enunciados

**Conjectura 1 (existência).** Para todo n ≥ 3, G(n) ≥ 1.

**Conjectura 2 (crescimento).** G(n) → ∞ quando n → ∞.

**Versão certificada.** Para todo n ≥ 3 existe um corte bom em que P e Q têm prova de primalidade: pelo teorema de Proth (P − 1 = k·2^m com k ímpar e k < 2^m) ou por serem menores que 2^64 (teste exato).

Observação: G(1) = G(2) = 0 e G(3) = 1, por isso o enunciado começa em n = 3.

## 5. Exemplos verificáveis à mão

| n | s | a | b | r | u | P | Q | N | w = N − P − Q | 4^n + 2^s − 1 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 4 | 3 | 2 | 1 | 5 | 1 | 13 | 23 | 299 | 263 | 263 |
| 5 | 3 | 1 | 2 | 7 | 1 | 7 | 173 | 1211 | 1031 | 1031 |
| 6 | 3 | 1 | 2 | 3 | 3 | 19 | 229 | 4351 | 4103 | 4103 |

Cheque o primeiro: t = 2n − s = 5, 2^5 + 1 = 33 = 3 · 11, então A = 3, B = 11, P = 2^2 · 3 + 1 = 13, Q = 2^1 · 11 + 1 = 23.

**Exemplo maior (n = 50, s = 91):** t = 9, A = 9, B = 57, a = 43, b = 48.

- P = 9 · 2^43 + 1 = 79164837199873
- Q = 57 · 2^48 + 1 = 16044073672507393
- N = P · Q = 1270126480306816285285011161089 (101 bits)
- Ambos primos com certificado de Proth, e N − P − Q = 4^50 + 2^91 − 1 (conferido).

Em n = 100 e n = 120 há exemplos com N de 201 e 241 bits, com P e Q certificados.

## 6. Evidência numérica

Teste exaustivo: para cada n, todos os cortes foram enumerados e testados (primalidade BPSW; certificado de Proth ou limite 2^64 para a versão certificada).

| faixa de n | média de G(n) | mínimo de G(n) | máximo | média certificada | esperado (heurística) | observado / esperado |
| --- | --- | --- | --- | --- | --- | --- |
| 4–20 | 11,4 | 1 (n = 4) | 19 | 11,4 | 12,8 | 0,89 |
| 21–40 | 22,9 | 15 (n = 24) | 31 | 22,1 | 28,7 | 0,80 |
| 41–80 | 34,8 | 24 (n = 48) | 50 | 21,1 | 42,7 | 0,82 |
| 81–120 | 41,4 | 22 (n = 110) | 63 | 23,5 | 54,7 | 0,76 |

Alguns valores individuais: G(4) = 1, G(5) = 4, G(10) = 11, G(20) = 14, G(40) = 24, G(60) = 36, G(100) = 36, G(120) = 39.

- **Existência:** nenhum n entre 3 e 200 ficou com G(n) = 0 (a contagem completa foi feita até n = 120; de 121 a 200 foi verificada só a existência de pelo menos um corte bom).
- **Versão certificada:** até n = 120, todo n tem ao menos um corte bom com P e Q provados.
- Os números acima são reproduzíveis com o notebook indicado na seção 9.

## 7. Heurística

O número de cortes possíveis para um dado n é da ordem de n² · log n (escolhas de s, de r entre os divisores ímpares de t, e de a). Para um primo "aleatório" ímpar x, a probabilidade de primalidade é cerca de 2/ln x. Como ln P + ln Q ≈ 2n · ln 2 em todo corte, cada corte tem probabilidade de ser bom pelo menos da ordem de 1/n². Definindo

```
E(n) = soma sobre os cortes de 4 / (ln P · ln Q),
```

a heurística sugere E(n) → ∞ (ao menos como log n), e G(n) deveria acompanhar E(n).

Os dados mostram G(n)/E(n) entre 0,76 e 0,89, caindo devagar. Isso indica que a heurística de independência superestima levemente, o que é esperado, porque P − 1 e Q − 1 compartilham estrutura (potências de 2 e os fatores de 2^t + 1) e isso altera as constantes. Não derivei a correção.

Para a conjectura ser falsa seria preciso que, para algum n, todo corte tivesse P ou Q composto, por exemplo por uma obstrução de cobertura por congruências (como nos números de Sierpiński e de Riesel para k·2^n ± 1 com k fixo). Aqui k varia com o corte e há muitos cortes; não encontramos obstrução alguma até n = 200.

## 8. Relação com resultados conhecidos

- **Teorema de Proth (1878):** se N = k·2^m + 1, k ímpar, k < 2^m, e existe a com a^((N−1)/2) ≡ −1 (mod N), então N é primo. Usado para certificar P e Q quando a > u e b é grande o bastante.
- **Fatores ciclotômicos de 2^t + 1:** a divisão em (2^u + 1) · B é o caso mais simples; há fatorações mais finas (polinômios ciclotômicos em 2), que não usamos e que dariam mais cortes.
- **Heurísticas de primos em famílias exponenciais** (tipo Hardy–Littlewood / Bateman–Horn) e os problemas de Sierpiński e Riesel são o contexto natural para estimar G(n).
- Não encontrei enunciado prévio exatamente igual a este, mas não fiz busca bibliográfica sistemática. Se algum leitor conhecer a referência, por favor avise.

## 9. Reprodutibilidade

Notebook: **conclusoes\_tuplas\_v4\_1.ipynb** (Python; roda no Google Colab sem instalação extra). O algoritmo:

1. Para n fixo, para cada s de 1 a 2n − 1, t = 2n − s.
2. Para cada divisor ímpar r ≥ 3 de t: u = t/r, A = 2^u + 1, B = (2^t + 1)/A.
3. Para cada a de 1 a s − 1: P = 2^a · A + 1, Q = 2^(s−a) · B + 1 (e a atribuição trocada, A ↔ B).
4. Se P e Q são primos (BPSW), registre o par e confira P·Q − P − Q = 4^n + 2^s − 1.
5. Para o certificado: Proth (k < 2^m) ou valor menor que 2^64.

A contagem por n, a comparação com E(n) e a busca de contraexemplo estão no notebook (parâmetro `NMAX`). Os testes até n = 120 levam cerca de meio minuto com sympy.

## 10. Perguntas abertas

1. **Existência para infinitos n:** é possível provar G(n) ≥ 1 para infinitos n? Parece exigir resultados sobre primos em famílias exponenciais que talvez estejam fora de alcance.
2. **Assintótica de G(n):** qual a ordem de crescimento e a constante correta, corrigindo a heurística de independência?
3. **Obstruções:** existe alguma obstrução aritmética (cobertura por congruências) que impeça G(n) ≥ 1 para algum n grande?
4. **Variantes:** usar fatores ciclotômicos mais finos de 2^t + 1; outras formas de w; outras bases além de 2.
5. **Estrutura do N:** como p − 1 = 2^a · (2^u + 1) é muito especial, esses N podem ser vulneráveis ao método p − 1 de Pollard? Não testado.

## Nota final

Este texto apresenta uma conjectura numérica, não uma prova. A ideia de que a construção se repete em cada faixa binária, com p crescendo junto com n, é de Bruno Paiva Viana; a enumeração, os testes e a redação formal foram feitos com assistência computacional do Claude.
