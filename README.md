# jogo-pedra-papel-tesoura
material aula Designer Profissional
O jogo terá:
- 🦸 Personagem animado representando o jogador.
- 🤖 Robô representando o computador.
- ✨ Animações de vitória, derrota e empate.
- ⚔️ Efeito de batalha entre personagens.
- 🎉 Efeitos de comemoração.
- 🔊 Sons para os resultados.
- 🏆 Placar automático.
- 🔄 Botão para reiniciar.
- 🎨 Layout moderno, colorido e responsivo.
1. Como montar no Replit
1. Entre em Replit.
2. Clique em Create Repl.
3. Escolha HTML, CSS, JS.
4. Abra o arquivo index.html.
5. Apague o conteúdo existente.
6. Cole o código completo abaixo.
7. Clique em Run.
2. Código completo do jogo
Projeto completo
 Pronto para Replit


<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pedra, Papel e Tesoura</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: #20234b;
    text-align: center;
    min-height: 100vh;
}

header {
    background: #17245f;
    color: white;
    padding: 25px 10px;
}

header h1 {
    font-size: clamp(25px, 5vw, 42px);
    margin: 5px;
}

header p {
    margin: 8px;
    font-size: 18px;
}

.container {
    max-width: 1050px;
    margin: 25px auto;
    background: white;
    border-radius: 25px;
    padding: 25px;
    width: 94%;
    box-shadow: 0 10px 30px #2225;
}

.escolhas {
    display: flex;
    justify-content: center;
    gap: 15px;
    flex-wrap: wrap;
    margin: 25px 0;
}

.escolhas button {
    border: none;
    border-radius: 18px;
    padding: 18px;
    width: 150px;
    color: white;
    font-size: 20px;
    font-weight: bold;
    cursor: pointer;
    transition: .25s;
}

.escolhas button:hover {
    transform: translateY(-7px) scale(1.04);
}

.pedra { background: #2678ed; }
.papel { background: #20bd78; }
.tesoura { background: #963be8; }

.escolhas span {
    display: block;
    font-size: 48px;
    margin-bottom: 8px;
}

.arena {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 25px;
    flex-wrap: wrap;
    margin: 35px 0;
}

.personagem {
    background: #f0efff;
    border-radius: 20px;
    padding: 20px;
    width: 220px;
    min-height: 210px;
}

.personagem h2 {
    margin: 5px;
}

.character {
    font-size: 85px;
    display: inline-block;
    animation: flutuar 2s infinite ease-in-out;
}

@keyframes flutuar {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-15px); }
}

.vitoria {
    animation: pular .4s infinite alternate !important;
}

@keyframes pular {
    to { transform: translateY(-30px) scale(1.2); }
}

.derrota {
    animation: tremer .3s 3 !important;
}

@keyframes tremer {
    25% { transform: translateX(-10px); }
    75% { transform: translateX(10px); }
}

.versus {
    font-size: 32px;
    font-weight: bold;
    color: #8044d9;
}

#message {
    background: #e7f9e6;
    padding: 20px;
    border-radius: 18px;
    font-size: 25px;
    font-weight: bold;
    margin: 20px auto;
    min-height: 70px;
}

.placar {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    background: #f1f0ff;
    padding: 20px;
    border-radius: 20px;
    gap: 15px;
}

.ponto {
    font-size: 23px;
    font-weight: bold;
}

.ponto span {
    display: block;
    font-size: 35px;
    margin-top: 8px;
}

#reset {
    background: #7036d8;
    color: white;
    padding: 15px 30px;
    border: none;
    border-radius: 15px;
    font-size: 18px;
    cursor: pointer;
    margin-top: 25px;
}

#reset:hover {
    background: #4d21a5;
    transform: scale(1.05);
}

.confete {
    position: fixed;
    top: -20px;
    font-size: 25px;
    pointer-events: none;
    animation: cair 2s linear forwards;
    z-index: 10;
}

@keyframes cair {
    to {
        transform: translateY(110vh) rotate(720deg);
        opacity: 0;
    }
}

footer {
    color: white;
    padding: 15px;
}

@media(max-width:600px) {
    .personagem {
        width: 42%;
        min-width: 130px;
    }

    .character {
        font-size: 60px;
    }

    .escolhas button {
        width: 105px;
        font-size: 16px;
    }

    .escolhas span {
        font-size: 35px;
    }

    .versus {
        width: 100%;
    }
}
</style>
</head>

<body>

<header>
    <h1>🎮 PEDRA, PAPEL E TESOURA</h1>
    <p>Prepare-se para a batalha!</p>
</header>

<div class="container">

    <h2>Escolha sua arma!</h2>

    <div class="escolhas">
        <button class="pedra" onclick="play('pedra')">
            <span>🪨</span>Pedra
        </button>

        <button class="papel" onclick="play('papel')">
            <span>📄</span>Papel
        </button>

        <button class="tesoura" onclick="play('tesoura')">
            <span>✂️</span>Tesoura
        </button>
    </div>

    <div class="arena">

        <div class="personagem">
            <h2>🦸 JOGADOR</h2>
            <div id="playerCharacter" class="character">🧑‍🚀</div>
            <p id="playerChoice">Você: -</p>
        </div>

        <div class="versus">⚡ VS ⚡</div>

        <div class="personagem">
            <h2>🤖 COMPUTADOR</h2>
            <div id="computerCharacter" class="character">🤖</div>
            <p id="computerChoice">Computador: -</p>
        </div>

    </div>

    <div id="message">
        Faça sua escolha e comece a batalha!
    </div>

    <h2>🏆 PLACAR</h2>

    <div class="placar">

        <div class="ponto">
            Vitórias
            <span id="wins">0</span>
        </div>

        <div class="ponto">
            Derrotas
            <span id="losses">0</span>
        </div>

        <div class="ponto">
            Empates
            <span id="draws">0</span>
        </div>

    </div>

    <button id="reset" onclick="resetGame()">
        🔄 Reiniciar jogo
    </button>

</div>

<footer>
    Desenvolvido com HTML, CSS e JavaScript ❤️
</footer>

<script>

let wins = 0;
let losses = 0;
let draws = 0;

const options = ["pedra", "papel", "tesoura"];

function play(player) {

    const computer =
        options[Math.floor(Math.random() * 3)];

    const playerCharacter =
        document.getElementById("playerCharacter");

    const computerCharacter =
        document.getElementById("computerCharacter");

    const message =
        document.getElementById("message");

    playerCharacter.className = "character";
    computerCharacter.className = "character";

    document.getElementById("playerChoice").textContent =
        "Você: " + player;

    document.getElementById("computerChoice").textContent =
        "Computador: " + computer;

    const emojis = {
        pedra: "🪨",
        papel: "📄",
        tesoura: "✂️"
    };

    playerCharacter.textContent = emojis[player];
    computerCharacter.textContent = emojis[computer];

    const venceu =
        (player === "pedra" && computer === "tesoura") ||
        (player === "papel" && computer === "pedra") ||
        (player === "tesoura" && computer === "papel");

    if (player === computer) {

        draws++;

        message.textContent = "🤝 EMPATE! Os dois são fortes!";

        playerCharacter.textContent = "🤝";
        computerCharacter.textContent = "🤝";

    } else if (venceu) {

        wins++;

        message.textContent = "🎉 VOCÊ VENCEU! PARABÉNS!";

        playerCharacter.textContent = "🦸";
        computerCharacter.textContent = "🤖";

        playerCharacter.classList.add("vitoria");
        computerCharacter.classList.add("derrota");

        confetes();

    } else {

        losses++;

        message.textContent = "😢 VOCÊ PERDEU! Tente novamente!";

        playerCharacter.textContent = "🧑‍🚀";
        computerCharacter.textContent = "👾";

        playerCharacter.classList.add("derrota");
        computerCharacter.classList.add("vitoria");

    }

    updateScore();
    playSound(player === computer ? "draw" : venceu ? "win" : "loss");
}

function updateScore() {

    document.getElementById("wins").textContent = wins;
    document.getElementById("losses").textContent = losses;
    document.getElementById("draws").textContent = draws;

}

function resetGame() {

    wins = 0;
    losses = 0;
    draws = 0;

    document.getElementById("message").textContent =
        "Faça sua escolha e comece a batalha!";

    document.getElementById("playerChoice").textContent =
        "Você: -";

    document.getElementById("computerChoice").textContent =
        "Computador: -";

    document.getElementById("playerCharacter").textContent = "🧑‍🚀";
    document.getElementById("computerCharacter").textContent = "🤖";

    document.getElementById("playerCharacter").className = "character";
    document.getElementById("computerCharacter").className = "character";

    updateScore();

}

function confetes() {

    const emojis = ["🎉", "⭐", "✨", "🏆", "🎊"];

    for (let i = 0; i < 35; i++) {

        const confete = document.createElement("div");

        confete.className = "confete";
        confete.textContent =
            emojis[Math.floor(Math.random() * emojis.length)];

        confete.style.left = Math.random() * 100 + "vw";
        confete.style.animationDelay = Math.random() * 0.8 + "s";

        document.body.appendChild(confete);

        setTimeout(() => confete.remove(), 3000);
    }

}

function playSound(type) {

    try {
        const audio = new AudioContext();

        const oscillator = audio.createOscillator();
        const gain = audio.createGain();

        oscillator.connect(gain);
        gain.connect(audio.destination);

        const frequencies = {
            win: 880,
            loss: 220,
            draw: 440
        };

        oscillator.frequency.value = frequencies[type];
        oscillator.type = "sine";

        gain.gain.setValueAtTime(0.15, audio.currentTime);
        gain.gain.exponentialRampToValueAtTime(
            0.001,
            audio.currentTime + 0.35
        );

        oscillator.start();
        oscillator.stop(audio.currentTime + 0.35);

        oscillator.onended = () => audio.close();

    } catch (error) {
        console.log("Áudio indisponível");
    }

}

</script>

</body>
</html>



3. O que você terá ao executar?








dribbble.com


Uma observação: os personagens deste código são emojis animados por CSS. Para ter personagens 3D de verdade, com braços, pernas, expressões faciais e movimentos de luta, será necessário adicionar personagens gráficos próprios.
