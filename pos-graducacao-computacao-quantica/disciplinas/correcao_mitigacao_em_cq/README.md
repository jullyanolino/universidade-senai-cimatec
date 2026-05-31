# Correção e Mitigação de Erros em Computação Quântica

**Pós-Graduação em Computação Quântica — SENAI/CIMATEC**  
**Grupo:** Davidson Clem · João Filipe Muchanga · José Hidalgo Suarez · Jullyano Lino

---

## Sobre o repositório

Este repositório contém os materiais práticos (*hands-on*) desenvolvidos para a disciplina de **Correção e Mitigação de Erros em Computação Quântica**. Os notebooks implementam, simulam e analisam duas grandes temáticas da computação quântica tolerante a falhas: o Código de Shor e as técnicas de tolerância a falhas via portas transversais e redundância de medições.

Todas as simulações utilizam **Qiskit 2.x** e **Qiskit Aer**, executadas em ambiente Python com análise estatística via NumPy, SciPy, Pandas e Seaborn.

---

## Conteúdo

### `CIMATEC_QEC_HandsOn1_Codigo_de_Shor.ipynb`

Implementação completa e análise do **Código de Shor [[9,1,3]]** — o primeiro código quântico capaz de corrigir erros arbitrários de qubit único.

**Seções:**

| # | Tópico |
|---|--------|
| 1 | Configuração do ambiente e verificação de dependências |
| 2 | Fundamentação teórica: ruído quântico e Código de Shor |
| 3 | Implementação do Código de Shor em Qiskit |
| 4 | Simulações e análise dos resultados |
| 5 | Modelo de ruído probabilístico e limiar de erro |
| 6 | Concatenação de códigos |
| 7 | Conclusões |

**Destaques técnicos:**

- Modelagem dos três canais de ruído de Pauli — bit-flip (X), phase-flip (Z) e bit-phase-flip (Y) — com visualização na esfera de Bloch.
- Implementação do codificador [[9,1,3]]: codificação em dois níveis com concatenação de repetição de amplitude e de fase, conforme os estados lógicos $|0_L\rangle$ e $|1_L\rangle$ do estabilizador de Shor.
- Identificação dos 8 geradores de estabilizadores ($g_1$–$g_8$) e circuitos de extração de síndrome correspondentes.
- Análise estatística com 4 096 shots por cenário, fidelidade via matriz de densidade, e curvas de limiar de erro (*threshold*) para cada tipo de ruído.
- Estudo de concatenação de códigos como estratégia de redução exponencial da taxa de erro.

---

### `CIMATEC_QEC_HandsOn2_Computacao_Quantica_Tolerante_a_Falhas.ipynb`

Implementação de operações **tolerantes a falhas** sobre qubits lógicos codificados, com foco em portas transversais do grupo de Clifford, extração de síndrome com ancillas e redundância de medições.

**Seções:**

| # | Tópico |
|---|--------|
| 1 | Base teórica: QEC, portas transversais, estabilizadores e redundância |
| 2 | Implementação: portas transversais e injeção de erros |
| 3 | Extração de síndrome e análise de redundância de medições |

**Destaques técnicos:**

- Implementação das portas lógicas transversais $X_L$, $Z_L$ e $CNOT_L$ sobre o código de repetição de 3 qubits e sobre o Código de Shor de 9 qubits, com verificação por simulação ideal.
- Injeção controlada de erros de Pauli em qubits específicos para os dois códigos, com análise dos efeitos sobre a síndrome.
- Circuitos de extração de síndrome com **qubits ancilla** para os estabilizadores $ZZ$ (bit-flip) e $XX$ (phase-flip).
- Modelagem de ruído nas medições das ancillas via `ReadoutError` e simulação do impacto de medições imperfeitas.
- **Redundância de medições e votação majoritária**: demonstração teórica e empírica da redução da probabilidade de erro com $R$ rodadas de medição, com comparação dos resultados entre o código de repetição e o Código de Shor.
- Discussão sobre o **Teorema de Eastin-Knill** e o custo da destilação de estados mágicos para a porta $T$ (não-Clifford), com análise do overhead do protocolo 15→1 de Bravyi–Kitaev para múltiplos níveis de destilação.
- Painel consolidado com 7 figuras cobrindo síndromes, curvas de confiabilidade e overhead de destilação.

---

## Pré-requisitos

```bash
pip install "qiskit>=2.3,<3.0" qiskit-aer matplotlib numpy scipy seaborn pandas tabulate pylatexenc
```

> Os notebooks incluem células de instalação automática das dependências via `pip`.

---

## Estrutura do repositório

```
.
├── CIMATEC_QEC_HandsOn1_Codigo_de_Shor.ipynb
├── CIMATEC_QEC_HandsOn2_Computacao_Quantica_Tolerante_a_Falhas.ipynb
└── README.md
```

---

## Referências

- GAITAN, F. *Quantum Error Correction and Fault Tolerant Quantum Computing*. CRC Press, 2008.
- ROFFE, J. Quantum error correction: an introductory guide. *Contemporary Physics*, 60(3), 2019.
- BRAVYI, S.; KITAEV, A. Universal quantum computation with ideal Clifford gates and noisy ancillas. *Physical Review A*, 71(2), 2005.
- IBM Quantum. *Foundations of quantum error correction*. IBM Quantum Learning, 2026.
- ALBERT, V. V. *et al.* Shor nine-qubit code. The Error Correction Zoo. <https://errorcorrectionzoo.org/c/shor_nine>
- FAIST, P. *Quantum error correction lecture notes*. Freie Universität Berlin, 2026.
- GUEDES, T. L. M. A short introduction to quantum error correction. *Brazilian Journal of Physics*, 56(2), 2026.
- SCURSULIM, J. V. S. *Computação quântica e teoria quântica de correção de erros* [Dissertação]. UFES, 2021.
