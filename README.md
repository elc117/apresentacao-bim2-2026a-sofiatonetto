# apresentacao-bim2-2026a-sofiatonetto
apresentacao-bim2-2026a-sofiatonetto created by GitHub Classroom

## Parte Prática

### Escolha do Ambiente e Execução
Fui tentar fazer no VS Code, pois não tenho mais a licença da Java IDE, mas estava com problemas, pois mesmo com todos as extensões necessárias já instaladas, não estava reconhecendo. Por esse motivo, fiz no **GitHub Codespaces** do meu repositório de apresentação.

Já no Codespace, criei os arquivos com o mesmo nome das `public class` do código para que o compilador reconhecesse e colei os códigos da aula. 

**Comandos utilizados:**
- Para compilar: `javac StudentGrades.java`
- Para executar: `java StudentGrades`

<img width="350" height="300" alt="Screen Recording 2026-05-10 at 18 31 03" src="https://github.com/user-attachments/assets/fe27a65c-f607-4ae8-acf4-13c9a572d671" />

### Evidências de Execução
* **Código 1:**
<img width="658" height="408" alt="Screen Recording 2026-05-10 at 18 42 16" src="https://github.com/user-attachments/assets/c6a28416-6d02-48f9-9c04-760346f953c4" />

* **Código 2:**
<img width="658" height="408" alt="Screen Recording 2026-05-10 at 18 54 36" src="https://github.com/user-attachments/assets/1b1281c0-3054-42fd-ad56-4217f3d8fe7c" />

* **Testando outras formas:**
<img width="658" height="408" alt="Screen Recording 2026-05-10 at 19 12 43" src="https://github.com/user-attachments/assets/1337f40e-e39d-4ae0-bfbc-78e65f931ce9" />

### Dificuldades
* GitHub: Durante um commit, ocorreu um problema de versionamento no meu github local e servidor, porque editei meu Readme e criei outros arquivos, então precisei sincronizar as versões. Para isso utilizei `git pull --rebase`.
* Execução: EU não tinha criado o arquivo `students.csv` então apareceu o erro do primeiro gif, então criei o arquivo e consegui executar o código.
* Execução: Após executar o código Generate e Student, o `students.csv` ficou vazio, percebi que isso aconteceu porque o código do GenerateStudentData criava uma planilha e colocava os 10 gerados na `morestudents.csv` por isso não aparecia nada e a média era 0. Então para testar alterei e executei novamente, obtendo resultado diferente (último gif). 

---

## Parte Teórica: Análise das Questões

### Do primeiro código:
**11 -> Em Java, strings são objetos da classe String. Identifique no código algumas operações que podemos fazer com strings.**
**15 -> Substitua student.getGrade() por student.grade. Explique o que acontece na compilação do código.**
**16 -> Se trocarmos o nome da classe StudentGrades por Main, teremos erro de compilação. O que fazer para trocar o nome e não ter erro de compilação?**

### Do segundo código:
**6 -> Encontre 2 linhas no código onde é feita a criação de algum objeto.**

---

## Parte Exploratória: 

* **URL do Código:** []
* **Trecho do Código:**
// 
# Referências:
* [Material aula 1 POO](https://liascript.github.io/course/?https://raw.githubusercontent.com/AndreaInfUFSM/elc117-2026a/main/classes/19/README.md#7)
