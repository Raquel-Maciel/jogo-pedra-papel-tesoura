# jogo-pedra-papel-tesoura
material aula Designer Profissional
let wins = 0;
let losses = 0;
let draws = 0;

function play(player) {
    const options = ["pedra", "papel", "tesoura"];

    const computer = options[
        Math.floor(Math.random() * options.length)
    ];

    document.getElementById("playerChoice").textContent =
        "Você: " + player;

    document.getElementById("computerChoice").textContent =
        "Computador: " + computer;

    const message = document.getElementById("message");

    if (player === computer) {
        message.textContent = "🤝 Empate!";
        draws++;
    } 
    else if (
        (player === "pedra" && computer === "tesoura") ||
        (player === "papel" && computer === "pedra") ||
        (player === "tesoura" && computer === "papel")
    ) {
        message.textContent = "🎉 Você venceu!";
        wins++;
    } 
    else {
        message.textContent = "😢 Você perdeu!";
        losses++;
    }

    updateScore();
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
        "Faça sua escolha!";

    document.getElementById("playerChoice").textContent =
        "Você: -";

    document.getElementById("computerChoice").textContent =
        "Computador: -";

    updateScore();
}
