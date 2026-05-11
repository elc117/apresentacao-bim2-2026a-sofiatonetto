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
- **`String.format()`**
```
return name + "," + id + "," + String.format("%.1f", grade);
```
- **`split(String regex)`**  
```
  String[] values = line.split(",");
```
- **`Double.parseDouble()`**  
```
  double grade = Double.parseDouble(values[2]);
```
- **Concatenação**  
```
  return name + "," + id + "," + String.format("%.1f", grade);
```
- **`String.valueOf()`**  
```
  String id = String.valueOf(1000 + i);
```
- **`indexOf(String)` e `indexOf(String, int)`**  
```
  int startIndex = json.indexOf("\"name\":") + 8;
  int firstNameIndex = json.indexOf("\"first\"", startIndex) + 9;
```
- **`substring(int begin, int end)`**  
```
  String firstName = json.substring(firstNameIndex, firstNameEnd);
  String lastName = json.substring(lastNameIndex, lastNameEnd);
```
- **`StringBuilder.append()` e `StringBuilder.toString()`**  
```
  StringBuilder response = new StringBuilder();
  response.append(line);
  return response.toString();
```
- **`BufferedReader.readLine()`**  
```
  String line = br.readLine();
  while ((line = br.readLine()) != null) { ... }
```

<br>

**16 -> Se trocarmos o nome da classe StudentGrades por Main, teremos erro de compilação. O que fazer para trocar o nome e não ter erro de compilação?**

Quando tem um código em Java, o nome do arquivo tem que ser o mesmo nome usado no `public class`. 

Para trocar o nome pode-se trocar o nome no código, então trocar `public class StudentGrades` por `public class Main`. Também pode-se renomear o arquivo, ou seja, o arquivo passa a se chamar `Main.java` não mais `StudentGrades.java`. Ou pode-se mudar a forma de comilar e executar o código: `javac Main.java` e `java Main`.

---

### Do segundo código:

**6 -> Encontre 2 linhas no código onde é feita a criação de algum objeto.**

- **Criação de um objeto `ArrayList`:**
```java
  List students = new ArrayList<>();
```
  É criado um objeto da classe `ArrayList`, que implementa a interface `List`, para armazenar os estudantes lidos do CSV.

- **Objeto `Student`:**
```
  Student student = new Student(name, id, grade);
```
Cria o objeto da classe `Student`, que chama o construtor que define e incializa os atributos: nome, id e nota lidos do arquivo CSV. 
  
---

## Parte Exploratória: 

* **URL do Código:** [E-commerce-project-springBoot](https://github.com/jaygajera17/E-commerce-project-springBoot)
* **Trecho do Código:**
```
@Controller
public class UserController {

	private final userService userService;
	private final productService productService;

	@Autowired
	public UserController(userService userService, productService productService) {
		this.userService = userService;
		this.productService = productService;
	}

	@GetMapping("/register")
	public String registerUser() {
		return "register";
	}

	@GetMapping("/buy")
	public String buy() {
		return "buy";
	}

	@GetMapping("/login")
	public ModelAndView userLogin(@RequestParam(required = false) String error) {
		ModelAndView mv = new ModelAndView("userLogin");
		if ("true".equals(error)) {
			mv.addObject("msg", "Please enter correct email and password");
		}
		return mv;
	}

	@GetMapping("/")
	public ModelAndView indexPage() {
		ModelAndView mView = new ModelAndView("index");
		String username = SecurityContextHolder.getContext().getAuthentication().getName();
		mView.addObject("username", username);
		List<Product> products = this.productService.getProducts();

		if (products.isEmpty()) {
			mView.addObject("msg", "No products are available");
		} else {
			mView.addObject("products", products);
		}
		return mView;
	}

	@GetMapping("/user/products")
	public ModelAndView getProducts() {

		ModelAndView mView = new ModelAndView("uproduct");

		List<Product> products = this.productService.getProducts();

		if (products.isEmpty()) {
			mView.addObject("msg", "No products are available");
		} else {
			mView.addObject("products", products);
		}

		return mView;
	}

	@PostMapping("newuserregister")
	public ModelAndView registerNewUser(@ModelAttribute User user) {
		boolean exists = this.userService.checkUserExists(user.getUsername());

		if (!exists) {
			user.setRole("ROLE_NORMAL");
			this.userService.addUser(user);
			return new ModelAndView("userLogin");
		} else {
			ModelAndView mView = new ModelAndView("register");
			mView.addObject("msg", user.getUsername() + " is taken. Please choose a different username.");
			return mView;
		}
	}

	@GetMapping("/profileDisplay")
	public String profileDisplay(Model model) {

		String username = SecurityContextHolder.getContext().getAuthentication().getName();
		User user = userService.getUserByUsername(username);

		if (user != null) {
			model.addAttribute("userid", user.getId());
			model.addAttribute("username", user.getUsername());
			model.addAttribute("email", user.getEmail());
			model.addAttribute("password", "");
			model.addAttribute("address", user.getAddress());
		} else {
			model.addAttribute("msg", "User not found");
		}

		return "updateProfile";
	}

	@PostMapping("/updateuser")
	public String updateUserProfile(@RequestParam("userid") int userid,
			@RequestParam("username") String username,
			@RequestParam("email") String email,
			@RequestParam("password") String password,
			@RequestParam("address") String address) {
		User updatedUser = this.userService.updateUserProfile(userid, username, email, password, address);
		if (updatedUser != null) {
			refreshAuthenticatedPrincipal(username);
		}
		return "redirect:/";
	}

	private void refreshAuthenticatedPrincipal(String username) {
		Authentication currentAuthentication = SecurityContextHolder.getContext().getAuthentication();
		Authentication newAuthentication = new UsernamePasswordAuthenticationToken(
				username,
				currentAuthentication.getCredentials(),
				currentAuthentication.getAuthorities());
		SecurityContextHolder.getContext().setAuthentication(newAuthentication);
	}

}
```
# Referências:
* [Material aula 1 POO](https://liascript.github.io/course/?https://raw.githubusercontent.com/AndreaInfUFSM/elc117-2026a/main/classes/19/README.md#7)
* [String em Java](https://www.devmedia.com.br/trabalhando-com-string-string-em-java/21737)
* [Strings e Java](https://www.devmedia.com.br/string-em-java-entendendo-e-utilizando-essa-classe/25503?utm_dev=google_ads_pmax&gad_source=1&gad_campaignid=22326280955&gbraid=0AAAAADrVyXFMgoL1TqNUefVs3dqW8U84K&gclid=Cj0KCQjw2YDQBhD_ARIsAE1qeSfFeTPUqMqHY_OcThJfmwoNEm58WpaLUpGcT2AxwxIiYO7vm1tn7TcaAtQgEALw_wcB)
