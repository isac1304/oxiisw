<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SEGREDINHO</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body, html { height: 100%; font-family: 'Poppins', sans-serif; overflow: hidden; background: #000; }

        /* TELA DE LOGIN - FOTO DE CAPA */
        #login-screen {
            position: fixed; width: 100%; height: 100%;
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('ig.jpg') center/cover;
            display: flex; align-items: center; justify-content: center; z-index: 1000;
            transition: transform 1s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .login-box {
            background: rgba(255, 255, 255, 0.1); backdrop-filter: blur(15px);
            padding: 40px; border-radius: 20px; border: 1px solid rgba(255,255,255,0.2);
            text-align: center; color: white; box-shadow: 0 25px 50px rgba(0,0,0,0.3);
        }
        .login-box h1 { font-family: 'Dancing Script', cursive; font-size: 2.5rem; margin-bottom: 20px; }
        input { 
            padding: 12px 20px; border-radius: 25px; border: none; outline: none;
            width: 100%; text-align: center; font-size: 1rem; margin-bottom: 15px;
        }
        button {
            background: #ff4757; color: white; border: none; padding: 12px 30px;
            border-radius: 25px; font-weight: 600; cursor: pointer; transition: 0.3s;
        }
        button:hover { background: #ff6b81; transform: scale(1.05); }

        /* CONTEÚDO DO SITE */
        #main-content {
            height: 100vh; width: 100%;
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url('carro.jpg') center/cover;
            display: none; justify-content: center; align-items: center; padding: 20px;
        }
        .letter-card {
            background: white; max-width: 500px; width: 100%;
            padding: 40px; border-radius: 15px; position: relative;
            box-shadow: 0 30px 60px rgba(0,0,0,0.5); text-align: center;
            animation: fadeIn 2s ease;
        }
        .my-photo {
            width: 130px; height: 130px; border-radius: 50%;
            border: 5px solid white; object-fit: cover;
            position: absolute; top: -65px; left: 50%; transform: translateX(-50%);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }
        .letter-card h2 { margin-top: 50px; color: #ff4757; font-family: 'Dancing Script', cursive; font-size: 2rem; }
        .message { margin-top: 20px; color: #444; line-height: 1.6; font-size: 1.05rem; }
        
        @keyframes fadeIn { from { opacity: 0; transform: scale(0.9); } to { opacity: 1; transform: scale(1); } }
    </style>
</head>
<body>

    <audio id="love-song" loop>
        <source src="/musica/Lil Uzi Vert- 20 Min (Instrumental) - Northside Music (youtube).mp3" type="audio/mpeg">
    </audio>

    <div id="login-screen">
        <div class="login-box">
            <h1>BEM VINDO </h1>
            <p>Para entrar, digite a senha :</p>
            <input type="text" id="password" placeholder="DD/MM/AAAA">
            <br>
            <button onclick="checkAccess()">Abrir </button>
        </div>
    </div>

    <div id="main-content">
        <div class="letter-card">
            <img src="flor.jpg" alt="Minha Foto" class="my-photo">
            <h2>Minha Carta de Amor</h2>
            <div class="message">
                <p>"Desde que você entrou na minha vida, tudo faz mais sentido.Você foi a melhor coisa que já aconteceu na minha vida Desdo do primeiro dia que eu te conheci eu me apaixonei por você,E continuo apaixonado'. </p>
                <br>
                <p>Escrevo isso para que você nunca esqueça o quanto voce é importante para mim e o quanto eu te amo pra caralho pretinha. 
                    FICA COMIGO?
                    VOCE ACEITA NAMORAR COMIGO?"</p>
            </div>
            <p style="margin-top: 25px; font-weight: 600; color: #ff4757;">Amo você!</p>
        </div>
    </div>

    <script>
        function checkAccess() {
            const pass = document.getElementById('password').value;
            if (pass === "07/09/2006") {
                const audio = document.getElementById('love-song');
                audio.play();
                
                document.getElementById('login-screen').style.transform = 'translateY(-100%)';
                setTimeout(() => {
                    document.getElementById('login-screen').style.display = 'none';
                    document.getElementById('main-content').style.display = 'flex';
                }, 1000);
            } else {
                alert("Essa não é a nossa data... tente novamente ❤️");
            }
        }

        // Máscara automática para a data
        document.getElementById('password').addEventListener('input', function (e) {
            var x = e.target.value.replace(/\D/g, '').match(/(\d{0,2})(\d{0,2})(\d{0,4})/);
            e.target.value = !x[2] ? x[1] : x[1] + '/' + x[2] + (x[3] ? '/' + x[3] : '');
        });
    </script>
</body>
</html>
