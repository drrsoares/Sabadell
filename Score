<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulário Score de Sabadell - UTI</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                        'primary-dark': '#4a49b7'
                    }
                }
            }
        };

        // Detectar preferência de modo escuro
        if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
            document.documentElement.classList.add('dark');
        }
        
        window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', event => {
            if (event.matches) {
                document.documentElement.classList.add('dark');
            } else {
                document.documentElement.classList.remove('dark');
            }
        });
    </script>
</head>
<body class="bg-white dark:bg-gray-900 text-gray-800 dark:text-gray-200 min-h-screen">
    <div class="container mx-auto p-4 max-w-4xl">
        <h1 class="text-3xl font-bold text-center my-6 text-primary dark:text-primary">Score de Sabadell - UTI</h1>
        
        <!-- Formulário principal -->
        <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-6 mb-6">
            <h2 class="text-xl font-semibold mb-4">Dados do Paciente</h2>
            
            <form id="sabadellForm" class="space-y-4">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label for="nome" class="block text-sm font-medium mb-1">Nome do Paciente</label>
                        <input type="text" id="nome" name="nome" required 
                            class="w-full px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-md text-base
                            dark:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-primary">
                    </div>
                    <div>
                        <label for="registro" class="block text-sm font-medium mb-1">Registro Hospitalar</label>
                        <input type="text" id="registro" name="registro" required 
                            class="w-full px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-md text-base
                            dark:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-primary">
                    </div>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label for="dataInternacao" class="block text-sm font-medium mb-1">Data da Internação na UTI</label>
                        <input type="date" id="dataInternacao" name="dataInternacao" required 
                            class="w-full px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-md text-base
                            dark:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-primary">
                    </div>
                    <div>
                        <label for="dataAlta" class="block text-sm font-medium mb-1">Data da Alta da UTI</label>
                        <input type="date" id="dataAlta" name="dataAlta" required 
                            class="w-full px-3 py-2 border border-gray-300 dark:border-gray-600 rounded-md text-base
                            dark:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-primary">
                    </div>
                </div>
                
                <div class="mt-6">
                    <div class="flex items-center justify-between mb-4">
                        <h2 class="text-xl font-semibold">Score de Sabadell</h2>
                        <button type="button" id="infoBtn" class="text-primary hover:text-primary-dark focus:outline-none">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                        </button>
                    </div>
                    
                    <div class="space-y-3 mb-4">
                        <div>
                            <input type="radio" id="score0" name="scoreSabadell" value="0" required
                                class="w-4 h-4 text-primary focus:ring-primary">
                            <label for="score0" class="ml-2">
                                0 - Bom prognóstico a longo prazo (> 6 meses)
                            </label>
                        </div>
                        <div>
                            <input type="radio" id="score1" name="scoreSabadell" value="1"
                                class="w-4 h-4 text-primary focus:ring-primary">
                            <label for="score1" class="ml-2">
                                1 - Mau prognóstico a longo prazo (< 6 meses) com readmissão na UTI irrestrita
                            </label>
                        </div>
                        <div>
                            <input type="radio" id="score2" name="scoreSabadell" value="2"
                                class="w-4 h-4 text-primary focus:ring-primary">
                            <label for="score2" class="ml-2">
                                2 - Mau prognóstico a curto prazo (< 6 meses) com readmissão na UTI discutível
                            </label>
                        </div>
                        <div>
                            <input type="radio" id="score3" name="scoreSabadell" value="3"
                                class="w-4 h-4 text-primary focus:ring-primary">
                            <label for="score3" class="ml-2">
                                3 - Morte esperada durante a hospitalização
                            </label>
                        </div>
                    </div>
                    
                    <div class="p-4 bg-gray-100 dark:bg-gray-700 rounded-md mb-4">
                        <div class="flex justify-between items-center">
                            <span class="font-medium">Score Final:</span>
                            <span id="scoreFinal" class="text-xl font-bold">-</span>
                        </div>
                    </div>
                </div>
                
                <!-- Modal de Informações do Score -->
                <div id="infoModal" class="fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center hidden">
                    <div class="bg-white dark:bg-gray-800 rounded-lg shadow-xl p-6 max-w-2xl w-full max-h-[90vh] overflow-y-auto mx-4">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-xl font-bold text-primary dark:text-primary">Guia do Score de Sabadell</h3>
                            <button id="closeModal" class="text-gray-500 hover:text-gray-700 dark:text-gray-400 dark:hover:text-gray-200 focus:outline-none">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                                </svg>
                            </button>
                        </div>
                        <div class="space-y-6">
                            <div>
                                <h4 class="text-lg font-semibold mb-2 flex items-center text-green-600 dark:text-green-400">
                                    <span class="inline-block w-6 h-6 bg-green-600 dark:bg-green-500 text-white rounded-full text-center mr-2">0</span>
                                    Bom prognóstico a longo prazo
                                </h4>
                                <div class="pl-8 text-sm space-y-2">
                                    <p>Paciente com <strong>bom prognóstico</strong> a longo prazo (> 6 meses).</p>
                                    <p>Indica uma expectativa de sobrevida superior a 6 meses após a alta da UTI com boa qualidade de vida e/ou condição funcional.</p>
                                    <p>Pacientes que se recuperaram completamente ou quase completamente da sua doença aguda.</p>
                                </div>
                            </div>
                            
                            <div>
                                <h4 class="text-lg font-semibold mb-2 flex items-center text-yellow-600 dark:text-yellow-400">
                                    <span class="inline-block w-6 h-6 bg-yellow-600 dark:bg-yellow-500 text-white rounded-full text-center mr-2">1</span>
                                    Mau prognóstico a longo prazo com readmissão na UTI irrestrita
                                </h4>
                                <div class="pl-8 text-sm space-y-2">
                                    <p>Paciente com <strong>mau prognóstico a longo prazo</strong> (< 6 meses) com readmissão na UTI irrestrita.</p>
                                    <p>A expectativa de sobrevida é menor que 6 meses, mas se houver deterioração durante a hospitalização, o paciente seria elegível para readmissão na UTI sem restrições.</p>
                                    <p>Estes pacientes podem se beneficiar de cuidados intensivos novamente se necessário.</p>
                                </div>
                            </div>
                            
                            <div>
                                <h4 class="text-lg font-semibold mb-2 flex items-center text-orange-600 dark:text-orange-400">
                                    <span class="inline-block w-6 h-6 bg-orange-600 dark:bg-orange-500 text-white rounded-full text-center mr-2">2</span>
                                    Mau prognóstico a curto prazo com readmissão na UTI discutível
                                </h4>
                                <div class="pl-8 text-sm space-y-2">
                                    <p>Paciente com <strong>mau prognóstico a curto prazo</strong> (< 6 meses) com readmissão na UTI discutível.</p>
                                    <p>A possibilidade de readmissão na UTI é considerada caso a caso, levando em conta comorbidades, estado funcional e a natureza de qualquer deterioração aguda.</p>
                                    <p>Nestes casos, deve-se considerar uma abordagem mais conservadora e possíveis limitações nos esforços de reanimação.</p>
                                </div>
                            </div>
                            
                            <div>
                                <h4 class="text-lg font-semibold mb-2 flex items-center text-red-600 dark:text-red-400">
                                    <span class="inline-block w-6 h-6 bg-red-600 dark:bg-red-500 text-white rounded-full text-center mr-2">3</span>
                                    Morte esperada durante a hospitalização
                                </h4>
                                <div class="pl-8 text-sm space-y-2">
                                    <p>Indica que a <strong>morte do paciente é esperada durante a atual hospitalização</strong>, mesmo após a alta da UTI.</p>
                                    <p>Pacientes com doenças em estágio terminal ou condições irreversíveis onde não se espera recuperação.</p>
                                    <p>Nestes casos, o foco deve ser em cuidados paliativos e medidas de conforto, com indicação clara de não readmissão na UTI.</p>
                                </div>
                            </div>
                            
                            <div class="bg-gray-100 dark:bg-gray-700 p-4 rounded-md">
                                <h4 class="font-semibold mb-2">Uso Clínico do Score</h4>
                                <p class="text-sm">O Score de Sabadell é uma ferramenta prognóstica para avaliação de pacientes no momento da alta da UTI. Ele ajuda a equipe médica a classificar pacientes quanto ao seu prognóstico e a orientar decisões sobre futuras readmissões na UTI. Este escore foi validado em estudos multicêntricos e tem valor preditivo para mortalidade hospitalar e pós-alta.</p>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="flex flex-col md:flex-row gap-3 pt-4">
                    <button type="submit" 
                        class="px-4 py-2 bg-primary text-white rounded-md hover:bg-primary-dark focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2">
                        Registrar Paciente
                    </button>
                    <button type="button" id="exportBtn"
                        class="px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-green-600 focus:ring-offset-2">
                        Exportar para CSV
                    </button>
                    <label for="importFile" 
                        class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-600 focus:ring-offset-2 cursor-pointer text-center">
                        Importar CSV
                    </label>
                    <input type="file" id="importFile" accept=".csv" class="hidden">
                </div>
            </form>
        </div>
        
        <!-- Tabela de Pacientes -->
        <div class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-6">
            <h2 class="text-xl font-semibold mb-4">Pacientes Registrados</h2>
            <div class="overflow-x-auto">
                <table class="min-w-full divide-y divide-gray-200 dark:divide-gray-700">
                    <thead class="bg-gray-50 dark:bg-gray-700">
                        <tr>
                            <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Nome</th>
                            <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Registro</th>
                            <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Internação</th>
                            <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Alta</th>
                            <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 dark:text-gray-300 uppercase tracking-wider">Score</th>
                        </tr>
                    </thead>
                    <tbody id="patientTableBody" class="bg-white dark:bg-gray-800 divide-y divide-gray-200 dark:divide-gray-700">
                        <tr>
                            <td colspan="5" class="px-6 py-4 text-center text-sm text-gray-500 dark:text-gray-400">
                                Nenhum paciente registrado
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Guia de uso -->
        <div class="mt-6 text-sm text-gray-600 dark:text-gray-400">
            <h3 class="font-medium mb-2">Instruções:</h3>
            <ul class="list-disc pl-5 space-y-1">
                <li>Preencha todos os dados do paciente e selecione o Score de Sabadell apropriado</li>
                <li>Clique em "Registrar Paciente" para adicionar o paciente à lista</li>
                <li>Use "Exportar para CSV" para salvar os dados no seu dispositivo</li>
                <li>Para continuar com dados existentes, use "Importar CSV" para carregar um arquivo CSV previamente salvo</li>
            </ul>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Arrays para armazenar dados de pacientes
            let patients = [];
            
            // Elementos do DOM
            const form = document.getElementById('sabadellForm');
            const scoreInputs = document.querySelectorAll('input[name="scoreSabadell"]');
            const scoreFinalEl = document.getElementById('scoreFinal');
            const tableBody = document.getElementById('patientTableBody');
            const exportBtn = document.getElementById('exportBtn');
            const importFile = document.getElementById('importFile');
            
            // Elementos do modal de informações
            const infoBtn = document.getElementById('infoBtn');
            const infoModal = document.getElementById('infoModal');
            const closeModal = document.getElementById('closeModal');
            
            // Abrir modal de informações
            infoBtn.addEventListener('click', function() {
                infoModal.classList.remove('hidden');
                document.body.style.overflow = 'hidden'; // Prevenir scroll do body
            });
            
            // Fechar modal de informações
            closeModal.addEventListener('click', function() {
                infoModal.classList.add('hidden');
                document.body.style.overflow = ''; // Restaurar scroll
            });
            
            // Fechar modal ao clicar fora da janela de informações
            infoModal.addEventListener('click', function(e) {
                if (e.target === infoModal) {
                    infoModal.classList.add('hidden');
                    document.body.style.overflow = '';
                }
            });
            
            // Fechar modal ao pressionar ESC
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Escape' && !infoModal.classList.contains('hidden')) {
                    infoModal.classList.add('hidden');
                    document.body.style.overflow = '';
                }
            });
            
            // Atualizar score final ao selecionar
            scoreInputs.forEach(input => {
                input.addEventListener('change', function() {
                    scoreFinalEl.textContent = this.value;
                });
            });
            
            // Submeter formulário
            form.addEventListener('submit', function(e) {
                e.preventDefault();
                
                // Verificar se o score foi selecionado
                const selectedScore = document.querySelector('input[name="scoreSabadell"]:checked');
                if (!selectedScore) {
                    alert("Por favor, selecione um Score de Sabadell.");
                    return;
                }
                
                // Criar objeto do paciente
                const patient = {
                    nome: document.getElementById('nome').value,
                    registro: document.getElementById('registro').value,
                    dataInternacao: document.getElementById('dataInternacao').value,
                    dataAlta: document.getElementById('dataAlta').value,
                    score: selectedScore.value
                };
                
                // Adicionar à lista e atualizar tabela
                patients.push(patient);
                updateTable();
                
                // Limpar formulário
                form.reset();
                scoreFinalEl.textContent = "-";
                
                // Feedback ao usuário
                alert("Paciente registrado com sucesso!");
            });
            
            // Exportar para CSV
            exportBtn.addEventListener('click', function() {
                if (patients.length === 0) {
                    alert("Não há pacientes para exportar.");
                    return;
                }
                
                // Criar cabeçalho do CSV
                let csv = 'Nome,Registro,Data Internação,Data Alta,Score\n';
                
                // Adicionar cada paciente
                patients.forEach(patient => {
                    csv += `"${patient.nome}","${patient.registro}","${patient.dataInternacao}","${patient.dataAlta}","${patient.score}"\n`;
                });
                
                // Criar e baixar o arquivo
                const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
                const url = URL.createObjectURL(blob);
                const link = document.createElement('a');
                link.setAttribute('href', url);
                link.setAttribute('download', 'score_sabadell_' + new Date().toISOString().substring(0, 10) + '.csv');
                link.style.visibility = 'hidden';
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
            });
            
            // Importar CSV
            importFile.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (!file) return;
                
                const reader = new FileReader();
                reader.onload = function(e) {
                    try {
                        const contents = e.target.result;
                        const rows = contents.split('\n');
                        
                        // Pular cabeçalho
                        for (let i = 1; i < rows.length; i++) {
                            if (rows[i].trim() === '') continue;
                            
                            // Tratar campos com vírgulas dentro de aspas
                            let fields = [];
                            let field = '';
                            let inQuotes = false;
                            
                            for (let j = 0; j < rows[i].length; j++) {
                                const char = rows[i][j];
                                
                                if (char === '"') {
                                    inQuotes = !inQuotes;
                                } else if (char === ',' && !inQuotes) {
                                    fields.push(field);
                                    field = '';
                                } else {
                                    field += char;
                                }
                            }
                            
                            // Adicionar último campo
                            fields.push(field);
                            
                            // Remover aspas extras
                            fields = fields.map(f => f.replace(/^"|"$/g, ''));
                            
                            if (fields.length >= 5) {
                                patients.push({
                                    nome: fields[0],
                                    registro: fields[1],
                                    dataInternacao: fields[2],
                                    dataAlta: fields[3],
                                    score: fields[4]
                                });
                            }
                        }
                        
                        updateTable();
                        alert(`CSV importado com sucesso. Total de pacientes: ${patients.length}`);
                    } catch (error) {
                        console.error("Erro ao importar CSV:", error);
                        alert("Erro ao importar o arquivo CSV. Verifique o formato do arquivo.");
                    }
                };
                reader.readAsText(file);
            });
            
            // Atualizar tabela de pacientes
            function updateTable() {
                if (patients.length === 0) {
                    tableBody.innerHTML = `
                        <tr>
                            <td colspan="5" class="px-6 py-4 text-center text-sm text-gray-500 dark:text-gray-400">
                                Nenhum paciente registrado
                            </td>
                        </tr>
                    `;
                    return;
                }
                
                tableBody.innerHTML = '';
                patients.forEach(patient => {
                    // Formatação das datas para exibição
                    const formatDate = (dateStr) => {
                        const [year, month, day] = dateStr.split('-');
                        return `${day}/${month}/${year}`;
                    };
                    
                    // Descrição do score
                    let scoreDesc = '';
                    switch(patient.score) {
                        case '0': scoreDesc = 'Bom prognóstico'; break;
                        case '1': scoreDesc = 'Mau prognóstico longo prazo'; break;
                        case '2': scoreDesc = 'Mau prognóstico curto prazo'; break;
                        case '3': scoreDesc = 'Morte esperada'; break;
                    }
                    
                    const row = document.createElement('tr');
                    row.classList.add('hover:bg-gray-50', 'dark:hover:bg-gray-700');
                    row.innerHTML = `
                        <td class="px-6 py-4 whitespace-nowrap text-sm">${patient.nome}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm">${patient.registro}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm">${formatDate(patient.dataInternacao)}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm">${formatDate(patient.dataAlta)}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm">
                            <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium 
                                ${patient.score === '0' ? 'bg-green-100 text-green-800 dark:bg-green-800 dark:text-green-100' : 
                                 patient.score === '1' ? 'bg-yellow-100 text-yellow-800 dark:bg-yellow-800 dark:text-yellow-100' : 
                                 patient.score === '2' ? 'bg-orange-100 text-orange-800 dark:bg-orange-800 dark:text-orange-100' : 
                                 'bg-red-100 text-red-800 dark:bg-red-800 dark:text-red-100'}">
                                ${patient.score} - ${scoreDesc}
                            </span>
                        </td>
                    `;
                    tableBody.appendChild(row);
                });
            }
        });
    </script>
</body>
</html>
