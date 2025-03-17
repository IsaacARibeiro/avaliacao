<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Avaliação TAD</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <script>
        function atualizarAvaliacao() {
            const pesosFonte = { "sim": 2, "nao": 0, "alta": 2, "media": 1, "baixa": 0 };
            const pesosConteudo = { "alta": 2, "media": 1, "baixa": 0 };
            
            let autenticidade = document.querySelector('select[name="autenticidade"]').value;
            let confianca = document.querySelector('select[name="confianca"]').value;
            let competencia = document.querySelector('select[name="competencia"]').value;
            let coerencia = document.querySelector('select[name="coerencia"]').value;
            let compatibilidade = document.querySelector('select[name="compatibilidade"]').value;
            let semelhanca = document.querySelector('select[name="semelhanca"]').value;
            
            let pontuacaoFonte = pesosFonte[autenticidade] + pesosFonte[confianca] + pesosFonte[competencia];
            let classificacaoFonte = "F - Não avaliada";
            let motivoFonte = "Não foi possível avaliar a idoneidade da fonte com os dados fornecidos.";
            
            if (pontuacaoFonte >= 5) {
                classificacaoFonte = "A - Inteiramente idônea";
                motivoFonte = "A fonte foi considerada autêntica, altamente confiável e competente.";
            } else if (pontuacaoFonte === 4) {
                classificacaoFonte = "B - Normalmente idônea";
                motivoFonte = "A fonte é autêntica e possui um nível médio de confiança e competência.";
            } else if (pontuacaoFonte === 3) {
                classificacaoFonte = "C - Regularmente idônea";
                motivoFonte = "A fonte é autêntica, mas apresenta limitações na confiabilidade e competência.";
            } else if (pontuacaoFonte <= 2) {
                classificacaoFonte = "E - Inidônea";
                motivoFonte = "A fonte não pôde ser autenticada ou apresenta pouca confiabilidade.";
            }
            
            let pontuacaoConteudo = pesosConteudo[coerencia] + pesosConteudo[compatibilidade] + pesosConteudo[semelhanca];
            let classificacaoConteudo = "6 - Não avaliado";
            let motivoConteudo = "Não há informações suficientes para avaliar o conteúdo.";
            
            if (pontuacaoConteudo >= 5) {
                classificacaoConteudo = "1 - Confirmado por outras fontes";
                motivoConteudo = "O conteúdo foi coerente, compatível e corroborado por outras fontes.";
            } else if (pontuacaoConteudo === 4) {
                classificacaoConteudo = "2 - Provavelmente verdadeiro";
                motivoConteudo = "O conteúdo apresenta coerência e compatibilidade, mas sem total confirmação.";
            } else if (pontuacaoConteudo === 3) {
                classificacaoConteudo = "3 - Possivelmente verdadeiro";
                motivoConteudo = "O conteúdo faz sentido, mas carece de mais fontes confirmatórias.";
            } else if (pontuacaoConteudo === 2) {
                classificacaoConteudo = "4 - Duvidoso";
                motivoConteudo = "O conteúdo apresenta algumas inconsistências e poucas confirmações.";
            } else if (pontuacaoConteudo <= 1) {
                classificacaoConteudo = "5 - Improvável";
                motivoConteudo = "O conteúdo apresenta baixa coerência, tornando sua veracidade improvável.";
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
                        <option value="sim">Sim - A fonte pode ser verificada e tem origem confirmada.</option>
                        <option value="nao">Não - A fonte não pode ser autenticada.</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label class="form-label">Confiança da fonte:</label>
                    <select name="confianca" class="form-select" onchange="atualizarAvaliacao()">
                        <option value="alta">Alta - A fonte tem histórico de informações precisas e confiáveis.</option>
                        <option value="media">Média - A fonte já forneceu informações confiáveis, mas pode conter erros.</option>
                        <option value="baixa">Baixa - A fonte tem histórico de informações imprecisas ou duvidosas.</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label class="form-label">Competência da fonte:</label>
                    <select name="competencia" class="form-select" onchange="atualizarAvaliacao()">
                        <option value="alta">Alta - A fonte tem conhecimento especializado sobre o assunto.</option>
                        <option value="media">Média - A fonte tem algum conhecimento, mas pode ser limitada.</option>
                        <option value="baixa">Baixa - A fonte não tem experiência ou conhecimento suficiente.</option>
                    </select>
                </div>
                <h3>Avaliação do Conteúdo</h3>
                <div class="mb-3">
                    <label class="form-label">Coerência do conteúdo:</label>
                    <select name="coerencia" class="form-select" onchange="atualizarAvaliacao()">
                        <option value="alta">Alta - O conteúdo faz sentido lógico e não apresenta contradições.</option>
                        <option value="media">Média - O conteúdo faz sentido, mas há pequenas contradições.</option>
                        <option value="baixa">Baixa - O conteúdo apresenta inconsistências e contradições evidentes.</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label class="form-label">Compatibilidade do conteúdo:</label>
                    <select name="compatibilidade" class="form-select" onchange="atualizarAvaliacao()">
                        <option value="alta">Alta - O conteúdo é compatível com outros dados confiáveis.</option>
                        <option value="media">Média - O conteúdo tem algumas semelhanças com dados confiáveis.</option>
                        <option value="baixa">Baixa - O conteúdo não se alinha com outros dados confiáveis.</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label class="form-label">Semelhança do conteúdo:</label>
                    <select name="semelhanca" class="form-select" onchange="atualizarAvaliacao()">
                        <option value="alta">Alta - Outras fontes confiáveis confirmam esse conteúdo.</option>
                        <option value="media">Média - Há algumas fontes que indicam a veracidade do conteúdo.</option>
                        <option value="baixa">Baixa - Nenhuma outra fonte confiável confirma o conteúdo.</option>
                    </select>
                </div>
            </form>
        </div>
        <div class="card shadow p-4 mt-4" id="resultado">
            <h3 class="text-center">Resultado da Avaliação</h3>
            <p>Selecione as opções acima para visualizar a avaliação.</p>
        </div>
    </div>
</body>
</html>
