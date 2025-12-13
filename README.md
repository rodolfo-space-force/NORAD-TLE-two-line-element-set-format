# NORAD-TLE-two-line-element-set-format
Leitor e interpretador de TLE (Two-Line Element Set) NORAD

Este projeto em Python realiza a leitura, interpretação e exportação de dados de órbitas de satélites contidos em arquivos TLE (Two-Line Element Set), com suporte à identificação do nome do satélite, caso esteja presente como cabeçalho.

TLEs são formatos padronizados para descrever a posição orbital e os parâmetros de movimento de objetos espaciais. 

Este script permite extrair essas informações de maneira estruturada e salvar os dados em formato JSON para uso posterior.

---

##  Estrutura do Arquivo TLE

Um TLE é composto por duas linhas padronizadas (Line 1 e Line 2), podendo ser precedidas por uma linha com o nome do satélite. 

Exemplo:

```
STARLINK-34935
1 51049U 22002AZ  23344.50972222  .00000319  00000-0  15287-4 0  9993
2 51049  53.2170 352.5403 0001660  59.5515 300.5766 15.08875454 99462
```

---

##  Funcionalidades

-  Detecta automaticamente o nome do satélite, se fornecido na primeira linha.
-  Realiza o parsing das duas linhas do TLE com base nos campos definidos pela documentação NORAD.
-  Exporta os dados interpretados em formato JSON (`output.json`) para fácil integração com outros sistemas ou análises.

---

##  Como funciona

1. O script abre o arquivo TLE (por padrão `STARLINK-34935.txt`).
2. Verifica se a primeira linha contém o nome do satélite.
3. Separa as duas linhas principais do TLE.
4. Utiliza dicionários `line1_fields` e `line2_fields` para extrair os campos com precisão.
5. Exibe os resultados em formato legível no terminal.
6. Gera um arquivo `output.json` com todos os dados estruturados.

---

##  Campos interpretados

### Linha 1
| Posição | Campo                          |
|---------|--------------------------------|
| 1       | Line Number                    |
| 3–7     | Satellite Catalog Number       |
| 8       | Classification                 |
| 10–17   | International Designator       |
| 19–32   | Epoch                          |
| 34–43   | 1st Derivative of Mean Motion  |
| 45–52   | 2nd Derivative of Mean Motion  |
| 54–61   | BSTAR Drag Term                |
| 63      | Ephemeris/Element Set Type     |
| 65–68   | Element Set Number             |
| 69      | Checksum                       |

### Linha 2
| Posição | Campo                                     |
|---------|-------------------------------------------|
| 1       | Line Number                               |
| 3–7     | Satellite Catalog Number                  |
| 9–16    | Inclination (deg)                         |
| 18–25   | Right Ascension of Asc. Node (deg)        |
| 27–33   | Eccentricity (decimal point assumed)      |
| 35–42   | Argument of Perigee (deg)                 |
| 44–51   | Mean Anomaly (deg)                        |
| 53–63   | Mean Motion (rev/day)                     |
| 64–68   | Revolution Number at Epoch                |
| 69      | Checksum                                  |

---

Certifique-se de que o arquivo `STARLINK-34935.txt` esteja no mesmo diretório que o script ou altere o nome do arquivo no trecho abaixo:


##  Requisitos

- Python 3.x

---


##  Referências

- CelesTrak NORAD TLE Documentation: https://celestrak.org/NORAD/documentation/tle-fmt.php
- https://celestrak.org/Norad/elements/table.php?GROUP=stations&FORMAT=tle
- NASA: [What is a TLE?](https://www.nasa.gov/audience/forstudents/5-8/features/nasa-knows/what-is-a-tle-58.html)
- [Space-Track.org](https://www.space-track.org/) – Fonte oficial de TLEs para objetos espaciais


You can reach me at rmilhomem[at]gmail[dot]com or connect on [LinkedIn](https://www.linkedin.com/in/rodolfo-space-force/) for collaborations.


## Licença

Este projeto está licenciado sob a Licença MIT. Você pode usar, modificar e redistribuir este código livremente, desde que mencione o autor original.

[Clique aqui para ver a licença completa.](https://opensource.org/licenses/MIT)
[![MIT License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](https://opensource.org/licenses/MIT)

