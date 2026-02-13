<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Gincana - Equipes</title>

  <!-- 🔑 ESSENCIAL PARA MOBILE -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    /* RESET BÁSICO */
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      font-family: system-ui, Arial, sans-serif;
      background:
        linear-gradient(
          rgba(0, 0, 0, 0.20),
          rgba(0, 0, 0, 0.30)
        ),
        url("https://i.postimg.cc/SsdnSQ0R/Sem-Titulo-2.png");
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      color: white;
      text-align: center;
      padding: 20px;
    }

    .tela {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 20px;
    }

    input {
      width: 90%;
      max-width: 220px;
      padding: 14px;
      font-size: 16px; /* evita zoom automático em inputs no iOS */
      margin-bottom: 15px;
      border-radius: 6px;
      border: none;
    }

    button {
      padding: 14px 24px;
      font-size: 15px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }

    .resultado {
      display: none;
      color: white;
    }

    .resultado img {
      width: 280px;
      max-width: 90%;
      margin: 20px 0;
      animation: mascoteEntrada 0.5s ease-out;
    }

    @keyframes mascoteEntrada {
      from {
        transform: scale(0.5);
        opacity: 0;
      }
      to {
        transform: scale(1);
        opacity: 1;
      }
    }

    .voltar {
      background: white;
      color: black;
      margin-top: 20px;
    }

    /* 💻 AJUSTE PARA DESKTOP */
    @media (min-width: 768px) {
      body {
        padding: 70px 250px;
      }
    }
  </style>
</head>

<body>

<!-- TELA INICIAL -->
<div class="tela" id="telaInicial">
    <h1>⚠️ Ao pesquisar, utilize apenas letras minúsculas e sem acentuação. Caso não encontre pelo nome completo, informe apenas o primeiro nome e o sobrenome.</h1>
  
    <input type="text" id="nome" placeholder="Digite seu nome">
    <button onclick="buscarEquipe()">Pesquisar</button>
</div>

<!-- TELA RESULTADO -->
<div class="tela resultado" id="telaResultado">
    <h2 id="mensagem"></h2>
    <img id="mascote" alt="Mascote da equipe">
    <button class="voltar" onclick="voltar()">Voltar</button>
</div>

<script>
function buscarEquipe() {
    const nome = document.getElementById("nome").value.trim().toLowerCase();

    if (nome === "") {
        alert("Digite seu nome.");
        return;
    }

    // 🔹 PARTICIPANTES (EDITE AQUI)
    const participantes = {
        urso: [
        "guilherme picon",
        "julia analia",
        "helaine natalia matos verçosa",
        "anne lenise oliveira fontenele",
        "danuta de souza maia lima",
        "kayke negreiros saraiva",
        "agata hellen costa de oliveira",
        "davi luiz de souza lima",
        "debora gregorio de menezes",
        "ana livia cavalcante de andrade",
        "malu kouri do santo amorim",
        "leticia oliveira barros",
        "emily cailane da silva araujo",
        "lhawany silveira dos santos",
        "isabela juca ribeiro",
        "amanda karoline cabral de frança",
        "ana clara oliveira rodrigues",
        "rafael bastos",
        "joao tenorio lopes de oliveira abreu",
        "leandro elias firmino leite",
        "larissa lirio passos",
        "thiago ferreira de oliveira",
        "deborah raphaely silva mariano",
        "leticia zaffalon",
        "daiane azevedo joaquim",
        "andressa ferreira de oliveira",
        "joao malakai mangueira dos reis",
        "benicio wanderley araujo",
        "rebeca maia tavares",
        "vicente maia tavares", 
        "wellington albuquerque da silva",
        "michelly simas",
        "gabriel arruda",
        "pedro otavio oliveira suave",
        "izaque dos santos carneiro",
        "kaiki de lima rios",
        "samuel zaire",
        "maria eduarda soares araujo",
        "ana maria da costa almeida",
        "marcos samuel martins dias",
        "gabriel izaque dias lemos",
        "thalya almeida marques dos santos",
        "adriele dias de souza",
        "wilson jose guedes tavares",
        "paulo vinicius oliveira da silva",
        "kelvin eduardo silva nascimento",
        "celio roberto muniz da costa",
        "ana julia da silva velasquez",
        "adriny vitoria",
        "clara menezes",
        "lara rayelly cavalcante santos",
        "clivia da silva franco",
        "breno christoff da costa araujo",
        "gabriele carvalho dantas",
        "adriana santana",
        "joao gabriel lima de araujo", 
        "arthur monteiro maia de alencar",
        "thalita souza", 
        "jose arthur mota",
        "alaide pereira",
        "juliana rodrigues mendes",
        "mario antonio araujo da silva",
        "carlos eduardo melo"         
    ],
        leao: [
          "yara moura da silva",
        "debora brito nascimento",
        "hayssa vitoria pineiro lopes",
        "artur souza santana",
        "maria eduarda lima de oliveira",
        "nicolas oliveira",
        "eduarda de paula bruschi",
        "rebeca de almeida da cunha",
        "nubia marques de almeida",
        "ane beatriz nascimento figueiredo",
        "camile cavalcante da conceiçao",
        "aime de castro carioca",
        "marcela arruda de andrade",
        "rayka beatriz",
        "maria eduarda gomes abugoche",
        "isis de lima zumba",
        "ryan esdras gouveia de lima",
        "lorena samara cruz varela",
        "sidney bernardo moura fernandes",
        "thais souza dos santos",
        "vinicius de souza monteiro",
        "higo filemon farias charife",
        "pedro henrique freitas de matos",
        "leonardo contreiras",
        "maria luiza gomes taveira",
        "ana vitoria bezerra freire",
        "vinicius sousa santos",
        "alanna da costa negreiros",
        "pedro henrique iafuri de araujo",
        "julya das neves e silva",
        "cecilia leal",
        "eduarda oliveira",
        "vitor de oliveira",
        "evelyn guimaraes",
        "isaac de castro",
        "luana ribeiro da silva",
        "camilly vitoria de lima paula",
        "roniel de souza dias",
        "anna livia marreiros de almeida",
        "joao gabriel oliveira dias",
        "rames cesar de araujo mesquita",
        "calebe samuel de araujo mesquita",
        "vytor henrique melgar de araujo",
        "janaina barroso cardoso",
        "janayra kessia batista santos",
        "thailon dos santos costa",
        "anna beatriz carvalho argolo",
        "camilly vitoria paiva pereira",
        "kelvin lieberman dos santos de oliveira",
        "herbert lieberman lima de oliveira",
        "calebe carvalho de mesquita",
        "calebe alencar da silva",
        "kelly juliana silva de souza",
        "sara maria ico rodrigues da silva",
        "davi pereira",
        "lunna isis gomes fonseca",
        "natharca reis",
        "joao gabriel melo"
    ],
        lobo: [
        "gabriela mariano",
        "maria eduarda araujo viana",
        "hanna carolina pinheiro lopes",
        "eduarda valentini verçosa gadelha",
        "isaque vitor",
        "kathyene de paula fernandes",
        "ysabelle de holanda ferreira",
        "gustavo mota",
        "eduarda hadassa anute",
        "ana lauren cavalcante de andrade",
        "anelise batista da silva",
        "ana clivia vidal russo",
        "iasmin evellyn feitosa dos santos",
        "fernanda garcia da silva",
        "eloah nascimento costa",
        "joao pedro souza vesque",
        "alanna victoria carvalho de frança",
        "giovana faria",
        "joao vitor da costa matias",
        "ana angelina",
        "lucas xavier",
        "gabriel rebouças",
        "arthur albuquerque de almeida",
        "juarez moura de souza neto",
        "ana flavia pereira",
        "jessica ellen",
        "hiann augusto sena de oliveira",
        "alexia de albuquerque",
        "beatriz araujo santos",
        "miguel anute",
        "maria nilce amancio",
        "ana flavia pereira",
        "urias gabriel",
        "elias maia barros",
        "jose rynaldo paiva muniz",
        "luna isabele dias menezes",
        "sara rodrigues dos santos",
        "ariadna dias de souza",
        "isabelly ripardo sena",
        "gabriel duarte queiroz",
        "danyelle damasckline chaves dos santos",
        "bernado maciel amorim",
        "alicia maria",
        "rafael ferreira de carvalho",
        "kalebe mateus de abreu muniz",
        "jose raimundo de souza amorim",
        "ana luiza alves do santos",
        "ester menezes",
        "pedro maciel",
        "elisson de souza almeida",
        "alicia vitoria maia de almeida",
        "emanuelle macedo",
        "bernardo maciel amorim",
        "davi lucas de almeida cunha",
        "eloa maria enes de souza",
        "leticia mariah",
        "luis felipe miranda gomes",
        "vinicius almeida de souza",
        "mariana gomes",
        "raqueline pereira",
        "karoline lima",
        "anny heloisa costa de lima",
        "isabela bello"   
    ],
aguia: [
        "hyanna beatriz",
        "maria isabel santos",
        "agata castro",
        "geovana brana",
        "adriel cordeiro rodrigues",
        "laura de paula brusque",
        "vitoria rodrigues do nascimento",
        "luiza de queiros freire",
        "ana clara oliveira de souza moraes",
        "julia rodrigues do nascimento",
        "liz da silva viga",
        "maria klara cavalcante rodrigues",
        "tamyres mendes de lima",
        "ana clara vilela de souza",
        "arthur de queiros figueiredo",
        "mel reatequim dias",
        "guilherme bastos",
        "camila stephanie araujo do couto",
        "rebeca freitas araujo",
        "matheus vinicius pimentel medeiros",
        "romulo moraes de souza",
        "emannuel abisai dos santos macedo",
        "samuel sean gouveia de lima",
        "lorena holanda",
        "luisa aguiar de oliveira",
        "adriana de souza lima",
        "isadora barros alarcon",
        "ryan souza de oliveira",
        "paulo vitor barbosa jansen",
        "sofia ortiz de souza",
        "alicia vitoria freitas guedes",
        "isabelly de arruda",
        "alana gabriele",
        "ana leticia lopes",
        "cawan damasceno de araujo",
        "pedro henrique lima de araujo",
        "matheus zaire",
        "calebe rodrigues dos santos",
        "gabriel barros vilas boas",
        "emanuelle vitoria ticona rodrigues",
        "gabriel oliveira lima vera rodrigues",
        "gabriel oliveira lima verde",
        "thalya almeida dos santos",
        "rakel holanda da costa oliveira",
        "maike henry oliveira agostinho",
        "wescley felipe soares de souza",
        "pedro otavio oliveira silva",
        "hykhara vitoria saraiva de araujo",
        "joao victor felix ximenes",
        "kevila lieberman dos santos de oliveira",
        "ana clara silva nascimento",
        "murilo monteiro maia de alencar",
        "pablo bertoldo pimenta",
        "larissa vitoria",
        "alice guimaraes",
        "amanda pereira",
        "thaua da silva cacela",
        "luana cordeiro rodrigues",
        "geovana bello",
        "paulo vinicius oliveira suave",
        "clauber rafael",
        "alana julia dias da silva"  
    ]
      
    };

    // 🔹 EQUIPES + IMAGENS (SEUS LINKS)
    const equipes = {
        urso: {
            nome: "Equipe Urso 🐻",
            cor: "#f6a028",
            mascote: "https://i.postimg.cc/SjbJHxtG/urso.png"
        },
        leao: {
            nome: "Equipe Leão 🦁",
            cor: "#ff5a10",
            mascote: "https://i.postimg.cc/RC6XtCK8/leao.png"
        },
        lobo: {
            nome: "Equipe Lobo 🐺",
            cor: "#ff020c",
            mascote: "https://i.postimg.cc/RVtskC0m/lobo.png"
        },
        aguia: {
            nome: "Equipe Águia 🦅",
            cor: "#0064b2",
            mascote: "https://i.postimg.cc/rwPLpPMb/aguia.png"
        }
    };

    let equipeEncontrada = null;

    for (let equipe in participantes) {
        if (participantes[equipe].includes(nome)) {
            equipeEncontrada = equipe;
            break;
        }
    }

    if (!equipeEncontrada) {
        alert("Nome não encontrado. Procure a organização.");
        return;
    }

    const dados = equipes[equipeEncontrada];

    document.getElementById("mensagem").innerText =
        `${nome.toUpperCase()}, você faz parte da ${dados.nome}!`;

    document.getElementById("mascote").src = dados.mascote;
    document.getElementById("telaResultado").style.backgroundColor = dados.cor;

    document.getElementById("telaInicial").style.display = "none";
    document.getElementById("telaResultado").style.display = "flex";
}

function voltar() {
    document.getElementById("telaResultado").style.display = "none";
    document.getElementById("telaInicial").style.display = "flex";
    document.getElementById("nome").value = "";
}
</script>

</body>
</html>
