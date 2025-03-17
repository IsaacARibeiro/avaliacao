<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Avaliação TAD</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <script>
        function atualizarAvaliacao() {
            let autenticidade = document.querySelector('select[name="autenticidade"]').value;
            let confianca = document.querySelector('select[name="confianca"]').value;
            let competencia = document.querySelector('select[name="competencia"]').value;
            let coerencia = document.querySelector('select[name="coerencia"]').value;
            let compatibilidade = document.querySelector('select[name="compatibilidade"]').value;
            let semelhanca = document.querySelector('select[name="semelhanca"]').value;

            let classificacaoFonte = "F - Idoneidade não avaliada";
            let motivoFonte = "Não há dados suficientes para avaliar a idoneidade da fonte.";

            if (autenticidade === "total" && confianca === "alta" && competencia === "alta") {
                classificacaoFonte = "A - Inteiramente idônea";
                motivoFonte = "Fonte autêntica, altamente confiável e tecnicamente competente.";
            } else if (autenticidade === "total" && confianca === "media" && competencia !== "baixa") {
                classificacaoFonte = "B - Normalmente idônea";
                motivoFonte = "Fonte autêntica com confiança média e competência aceitável.";
            } else if (autenticidade === "total" && confianca === "baixa" || competencia === "baixa") {
                classificacaoFonte = "C - Regularmente idônea";
                motivoFonte = "Fonte autêntica, mas apresenta baixa confiança ou competência.";
            } else if (autenticidade === "parcial") {
                classificacaoFonte = "D - Normalmente inidônea";
                motivoFonte = "Autenticidade parcial, podendo conter informações duvidosas.";
            } else if (autenticidade === "nao") {
                classificacaoFonte = "E - Inidônea";
                motivoFonte = "Fonte não autêntica, comprometendo a confiabilidade dos dados.";
            }

            let classificacaoConteudo = "6 - Veracidade não avaliada";
            let motivoConteudo = "Não há dados suficientes para avaliar a credibilidade do conteúdo.";

            if (coerencia === "alta" && compatibilidade === "alta" && semelhanca === "alta") {
                classificacaoConteudo = "1 - Confirmado por outras fontes independentes";
                motivoConteudo = "Conteúdo coerente, compatível e confirmado por múltiplas fontes independentes.";
            } else if ((coerencia === "alta" || compatibilidade === "alta") && semelhanca !== "baixa") {
                classificacaoConteudo = "2 - Provavelmente verdadeiro";
                motivoConteudo = "Conteúdo bem estruturado e com evidências parciais de outras fontes.";
            } else if (coerencia === "media" && compatibilidade === "media" && semelhanca === "media") {
                classificacaoConteudo = "3 - Possivelmente verdadeiro";
                motivoConteudo = "Conteúdo apresenta pontos de coerência e compatibilidade, mas sem confirmação clara.";
            } else if (coerencia === "baixa" || compatibilidade === "baixa") {
                classificacaoConteudo = "4 - Duvidoso";
                motivoConteudo = "Conteúdo com contradições e pouca compatibilidade com dados confiáveis.";
            } else if (coerencia === "baixa" && compatibilidade === "baixa" && semelhanca === "baixa") {
                classificacaoConteudo = "5 - Improvável";
                motivoConteudo = "Conteúdo incoerente, incompatível e sem confirmação de fontes confiáveis.";
            }

            document.getElementById("resultado").innerHTML = `
                <h3 class="text-center">Resultado da Avaliação</h3>
                <p><strong>Classificação da Fonte:</strong> ${classificacaoFonte}</p>
                <p>${motivoFonte}</p>
                <p><strong>Classificação do Conteúdo:</strong> ${classificacaoConteudo}</p>
                <p>${motivoConteudo}</p>
            `;
        }
    </script>
</head>
<body class="bg-light">
    <div class="container mt-5">
        <div class="card shadow p-4">
            <h2 class="text-center mb-4">Formulário de Avaliação TAD</h2>
            <form>
                <h3>Avaliação da Fonte</h3>
                <div class="mb-3">
                    <label class="form-label">Autenticidade da fonte:</label>
                    <select name="autenticidade" class="form-select" onchange="atualizarAvaliacao()">
                        <option value="total">Totalmente autêntica - A fonte pode ser verificada e sua origem é confirmada.</option>
                        <option value="parcial">Parcialmente autêntica - Existem dúvidas sobre a origem ou autenticidade da fonte.</option>
                        <option value="nao">Não autêntica - A fonte não pode ser verificada e sua origem é questionável.</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label class="form-label">Confiança da fonte:</label>
                    <select name="confianca" class="form-select" onchange="atualizarAvaliacao()">
                        <option value="alta">Alta - A fonte tem um histórico consistente de informações precisas e confiáveis.</option>
                        <option value="media">Média - A fonte já forneceu informações confiáveis, mas pode conter erros ocasionais.</option>
                        <option value="baixa">Baixa - A fonte tem histórico de informações imprecisas ou tendenciosas.</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label class="form-label">Competência da fonte:</label>
                    <select name="competencia" class="form-select" onchange="atualizarAvaliacao()">
                        <option value="alta">Alta - A fonte tem conhecimento especializado sobre o assunto.</option>
                        <option value="media">Média - A fonte tem algum conhecimento, mas pode ser limitada.</option>
                        <option value="baixa">Baixa - A fonte não tem experiência ou conhecimento suficiente no assunto.</option>
                    </select>
                </div>
            </form>
        </div>
        <div class="card shadow p-4 mt-4" id="resultado"></div>
    </div>
</body>
</html>
