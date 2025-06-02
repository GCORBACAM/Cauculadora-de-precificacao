<!DOCTYPE html>
<html>
<head>
    <title>Calculadora de Revenda</title>
    <style>
        body { font-family: Arial; margin: 20px; }
        input, button { padding: 8px; margin: 5px; }
    </style>
</head>
<body>
    <h2>Calculadora de Revenda</h2>
    
    <label>Valor do Produto (R$):</label>
    <input type="number" id="valorProduto" step="0.01"><br>
    
    <label>Imposto (%):</label>
    <input type="number" id="imposto" step="0.1"><br>
    
    <label>Taxa da Maquininha (%):</label>
    <input type="number" id="taxaMaquininha" step="0.1"><br>
    
    <button onclick="calcular()">Calcular Preço de Venda</button>
    
    <h3>Resultados:</h3>
    <div id="resultado"></div>

    <script>
        function calcular() {
            // Pegar valores dos inputs
            const valorProduto = parseFloat(document.getElementById("valorProduto").value);
            const imposto = parseFloat(document.getElementById("imposto").value) / 100;
            const taxaMaquininha = parseFloat(document.getElementById("taxaMaquininha").value) / 100;
            
            // Margens de lucro a serem calculadas
            const margens = [10, 20, 30, 40];
            let resultados = "";
            
            // Calcular para cada margem
            margens.forEach(margem => {
                const lucro = valorProduto * (margem / 100);
                const precoVenda = (valorProduto + lucro) / (1 - imposto - taxaMaquininha);
                
                resultados += `<p><strong>Margem ${margem}%:</strong> R$ ${precoVenda.toFixed(2)}</p>`;
            });
            
            // Mostrar resultados
            document.getElementById("resultado").innerHTML = resultados;
        }
    </script>
</body>
</html>
