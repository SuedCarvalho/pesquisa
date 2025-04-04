<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pesquisa de Satisfação - Leal Peças</title>
    <style>
        :root {
            --primary-color: #1E6F8C; /* Azul principal */
            --secondary-color: #2D936C; /* Verde principal */
            --accent-color: #3AB795; /* Verde claro */
            --text-color: #333333;
            --light-gray: #f5f5f5;
            --white: #ffffff;
            --border-color: #ddd;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-image: url('https://images.unsplash.com/photo-1507035895480-2b3156c31fc8?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            color: var(--text-color);
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 800px;
            margin: 30px auto;
            background: rgba(255, 255, 255, 0.92);
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(5px);
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid var(--secondary-color);
        }
        
        .logo {
            font-size: 28px;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 5px;
            letter-spacing: 1px;
        }
        
        .logo span {
            color: var(--secondary-color);
        }
        
        h1 {
            color: var(--primary-color);
            margin-bottom: 10px;
            font-size: 24px;
        }
        
        .description {
            color: #555;
            font-size: 16px;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .form-group {
            margin-bottom: 25px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--primary-color);
        }
        
        input[type="text"],
        input[type="tel"],
        textarea,
        select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            font-size: 16px;
            transition: all 0.3s;
            background-color: var(--light-gray);
        }
        
        input[type="text"]:focus,
        input[type="tel"]:focus,
        textarea:focus,
        select:focus {
            border-color: var(--secondary-color);
            outline: none;
            box-shadow: 0 0 0 3px rgba(46, 147, 108, 0.2);
            background-color: var(--white);
        }
        
        textarea {
            min-height: 120px;
            resize: vertical;
        }
        
        .rating-scale {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
            gap: 8px;
        }
        
        .rating-option {
            text-align: center;
            flex: 1;
        }
        
        .rating-option input {
            display: none;
        }
        
        .rating-option label {
            display: block;
            padding: 12px 5px;
            background: var(--light-gray);
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 600;
        }
        
        .rating-option input:checked + label {
            background: var(--secondary-color);
            color: var(--white);
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        
        .rating-option:hover label {
            background: #e0e0e0;
        }
        
        .rating-option input:checked:hover + label {
            background: var(--secondary-color);
        }
        
        .rating-labels {
            display: flex;
            justify-content: space-between;
            margin-top: 8px;
            font-size: 13px;
            color: #666;
        }
        
        .btn-submit {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: var(--white);
            border: none;
            padding: 15px 25px;
            font-size: 17px;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s;
            display: block;
            width: 100%;
            font-weight: 600;
            letter-spacing: 0.5px;
            text-transform: uppercase;
            margin-top: 20px;
            box-shadow: 0 4px 15px rgba(30, 111, 140, 0.3);
        }
        
        .btn-submit:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(30, 111, 140, 0.4);
            background: linear-gradient(135deg, var(--secondary-color), var(--primary-color));
        }
        
        .required-field::after {
            content: " *";
            color: #e74c3c;
        }
        
        .bike-icon {
            color: var(--secondary-color);
            margin-right: 8px;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 25px;
                margin: 15px;
            }
            
            .rating-scale {
                flex-wrap: wrap;
            }
            
            .rating-option {
                flex: 1 0 45%;
                margin-bottom: 8px;
            }
        }
        
        @media (max-width: 480px) {
            .container {
                padding: 20px 15px;
            }
            
            .logo {
                font-size: 24px;
            }
            
            h1 {
                font-size: 20px;
            }
            
            .rating-option {
                flex: 1 0 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">LEAL <span>PEÇAS</span></div>
            <h1><i class="bike-icon">🚲</i> Pesquisa de Satisfação</h1>
            <p class="description">Sua opinião é fundamental para continuarmos oferecendo os melhores produtos e serviços para o mundo das bicicletas.</p>
        </header>
        
        <form id="satisfactionForm">
            <div class="form-group">
                <label for="name" class="required-field">Nome</label>
                <input type="text" id="name" name="name" required placeholder="Seu nome completo">
            </div>
            
            <div class="form-group">
                <label for="whatsapp">WhatsApp</label>
                <input type="tel" id="whatsapp" name="whatsapp" placeholder="(00) 00000-0000">
            </div>
            
            <div class="form-group">
                <label for="how-found">Como você nos achou?</label>
                <select id="how-found" name="how-found">
                    <option value="">Selecione...</option>
                    <option value="instagram">Instagram</option>
                    <option value="google">Google</option>
                    <option value="facebook">Facebook</option>
                    <option value="indicacao">Indicação de amigo(a)</option>
                    <option value="outro">Outro meio</option>
                </select>
            </div>
            
            <div class="form-group" id="other-meio-group" style="display:none;">
                <label for="other-meio">Qual outro meio?</label>
                <input type="text" id="other-meio" name="other-meio" placeholder="Por favor, especifique">
            </div>
            
            <div class="form-group">
                <label for="department">Tipo de produto/serviço</label>
                <select id="department" name="department">
                    <option value="">Selecione...</option>
                    <option value="bike">Bike completa</option>
                    <option value="mountain-bike">Mountain Bike</option>
                    <option value="pecas">Peças para Bicicleta</option>
                    <option value="acessorios">Acessórios</option>
                    <option value="vestuario">Vestuário</option>
                    <option value="manutencao">Manutenção</option>
                    <option value="outro">Outro</option>
                </select>
            </div>
            
            <div class="form-group">
                <label class="required-field">Como você avalia a qualidade dos nossos produtos?</label>
                <div class="rating-scale">
                    <div class="rating-option">
                        <input type="radio" id="rating-1" name="quality_rating" value="1" required>
                        <label for="rating-1">1</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="rating-2" name="quality_rating" value="2">
                        <label for="rating-2">2</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="rating-3" name="quality_rating" value="3">
                        <label for="rating-3">3</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="rating-4" name="quality_rating" value="4">
                        <label for="rating-4">4</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="rating-5" name="quality_rating" value="5">
                        <label for="rating-5">5</label>
                    </div>
                </div>
                <div class="rating-labels">
                    <span>Muito Ruim</span>
                    <span>Excelente</span>
                </div>
            </div>
            
            <div class="form-group">
                <label class="required-field">Como você avalia o atendimento em nossa loja?</label>
                <div class="rating-scale">
                    <div class="rating-option">
                        <input type="radio" id="service-1" name="service_rating" value="1" required>
                        <label for="service-1">1</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="service-2" name="service_rating" value="2">
                        <label for="service-2">2</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="service-3" name="service_rating" value="3">
                        <label for="service-3">3</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="service-4" name="service_rating" value="4">
                        <label for="service-4">4</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="service-5" name="service_rating" value="5">
                        <label for="service-5">5</label>
                    </div>
                </div>
                <div class="rating-labels">
                    <span>Muito Ruim</span>
                    <span>Excelente</span>
                </div>
            </div>
            
            <div class="form-group">
                <label class="required-field">Você recomendaria a Leal Peças para outros ciclistas?</label>
                <div class="rating-scale">
                    <div class="rating-option">
                        <input type="radio" id="recommend-no" name="recommendation" value="Não" required>
                        <label for="recommend-no">Não</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="recommend-maybe" name="recommendation" value="Talvez">
                        <label for="recommend-maybe">Talvez</label>
                    </div>
                    <div class="rating-option">
                        <input type="radio" id="recommend-yes" name="recommendation" value="Sim">
                        <label for="recommend-yes">Sim</label>
                    </div>
                </div>
            </div>
            
            <div class="form-group">
                <label for="comments">O que podemos melhorar? Quais produtos gostaria de encontrar em nossa loja?</label>
                <textarea id="comments" name="comments" placeholder="Sua opinião é muito importante para nós..."></textarea>
            </div>
            
            <button type="submit" class="btn-submit">Enviar Pesquisa</button>
        </form>
    </div>
    
    <script>
        // Mostrar campo "Outro meio" quando selecionado
        document.getElementById('how-found').addEventListener('change', function() {
            const otherField = document.getElementById('other-meio-group');
            otherField.style.display = this.value === 'outro' ? 'block' : 'none';
        });

        // Máscara para WhatsApp
        document.getElementById('whatsapp').addEventListener('input', function(e) {
            let value = e.target.value.replace(/\D/g, '');
            if (value.length > 11) value = value.substring(0, 11);
            
            if (value.length > 0) {
                value = value.replace(/^(\d{2})(\d)/g, '($1) $2');
                if (value.length > 10) {
                    value = value.replace(/(\d{5})(\d)/, '$1-$2');
                } else {
                    value = value.replace(/(\d{4})(\d)/, '$1-$2');
                }
            }
            
            e.target.value = value;
        });

        // Envio do formulário
        document.getElementById('satisfactionForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Simulação de envio
            setTimeout(() => {
                alert('Obrigado por compartilhar sua opinião! Sua avaliação ajuda a Leal Peças a melhorar cada vez mais.');
                this.reset();
                document.getElementById('other-meio-group').style.display = 'none';
                
                window.scrollTo({
                    top: 0,
                    behavior: 'smooth'
                });
            }, 500);
        });
    </script>
</body>
</html>
