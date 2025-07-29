# botao
Ao clicá-lo, mudarão a frase e a cor do botão e de fundo, da página 



# botao-o-clique-aqui
Ao se clicar no botão, a frase descrita no botão e a c cor mudam.




<!DOCTYPE html>
<html lang="pt">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Relógio Digital</title>
    <style>
        body {
            background: linear-gradient(to right,#0c083f, #295db8);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            color: hsl(110, 98%, 54%);
            font-family: 'Segoe UI', sans-serif;
        }

        #clock {
            font-size: 48px;
            font-weight: bold;
        }
    </style>
</head>

<body>
    <h2>Desenvolvido por (Powered by): <br> Nediane Prazeres</h2>
    <h1>Relógio Digital</h1>

    <!-- Relógio -->
    <p id="clock"></p>

    <!-- Data atual -->
    <p id="data"></p>

    <!-- Previsão do tempo -->
    <p id="tempo"></p>

    <script>
        // Relógio digital
        function updateClock() {
            const now = new Date();
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            document.getElementById('clock').textContent = `${hours}:${minutes}:${seconds}`;
        }
        setInterval(updateClock, 1000);
        updateClock();

        // Data atual
        function atualizarData() {
            const agora = new Date();
            const dataFormatada = agora.toLocaleDateString('pt-BR', {
                weekday: 'long',
                year: 'numeric',
                month: 'long',
                day: 'numeric'
            });
            document.getElementById('data').textContent = dataFormatada;
        }
        atualizarData();

        // Previsão do tempo
        function carregarPrevisaoTempo() {
            const cidade = "Duque de Caxias";
            const chaveAPI = "SUA_CHAVE_AQUI"; // substitua pela sua chave da OpenWeatherMap

            fetch(`https://api.openweathermap.org/data/2.5/weather?q=${cidade}&appid=${chaveAPI}&units=metric&lang=pt_br`)
                .then(resposta => resposta.json())
                .then(dados => {
                    const temp = Math.round(dados.main.temp);
                    const descricao = dados.weather[0].description;
                    document.getElementById('tempo').textContent = `Tempo hoje: ${descricao}, ${temp}°C.`;
                })
                .catch(erro => {
                    document.getElementById('tempo').textContent = "Não foi possível carregar a previsão do tempo.";
                });
        }
        carregarPrevisaoTempo();
    </script>
</body>

</html>








script.js

const botao = document.querySelector('#botao');
if (botao) {
    botao.addEventListener('click', function () {
        document.body.style.backgroundColor = 'lightblue';
        botao.textContent = 'Você Clicou!';
        botao.style.backgroundColor = 'blue';
        botao.style.color = 'white';
    });
}
