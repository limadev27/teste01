# teste01
import React, { useState } from 'react';
import { ChevronRight, ChevronDown, Play, Book, Code, CheckCircle } from 'lucide-react';

const PythonBeginnerGuide = () => {
  const [activeSection, setActiveSection] = useState('intro');
  const [completedSections, setCompletedSections] = useState(new Set());
  const [codeOutput, setCodeOutput] = useState('');

  const sections = [
    { id: 'intro', title: 'Introdução ao Python', icon: Book },
    { id: 'variables', title: 'Variáveis e Tipos', icon: Code },
    { id: 'operators', title: 'Operadores', icon: Code },
    { id: 'conditions', title: 'Estruturas Condicionais', icon: Code },
    { id: 'loops', title: 'Loops', icon: Code },
    { id: 'functions', title: 'Funções', icon: Code },
    { id: 'lists', title: 'Listas', icon: Code },
    { id: 'practice', title: 'Exercícios Práticos', icon: Play }
  ];

  const content = {
    intro: {
      title: 'Por que Python?',
      theory: `Python é uma das linguagens mais populares para iniciantes por ser:
      
• **Fácil de ler**: Sintaxe clara e simples
• **Versátil**: Web, ciência de dados, automação, IA
• **Grande comunidade**: Muito suporte e recursos
• **Gratuito**: Totalmente open source`,
      code: `# Seu primeiro programa Python!
print("Olá, mundo!")
print("Bem-vindo ao Python! 🐍")`,
      explanation: 'O comando print() exibe texto na tela. É o jeito mais básico de mostrar resultados.'
    },
    
    variables: {
      title: 'Variáveis e Tipos de Dados',
      theory: `Variáveis são como "caixas" que guardam informações:

**Tipos principais:**
• **str** (texto): "João", "Python"
• **int** (números inteiros): 10, -5, 0
• **float** (números decimais): 3.14, -2.7
• **bool** (verdadeiro/falso): True, False`,
      code: `# Criando variáveis
nome = "Ana"              # string (texto)
idade = 25                # int (número inteiro)
altura = 1.65             # float (número decimal)
estudante = True          # bool (verdadeiro/falso)

# Mostrando os valores
print(f"Nome: {nome}")
print(f"Idade: {idade} anos")
print(f"Altura: {altura}m")
print(f"É estudante? {estudante}")

# Verificando o tipo
print(f"Tipo da variável nome: {type(nome)}")`,
      explanation: 'Use nomes descritivos para variáveis. O f-string (f"...") é uma forma moderna de inserir variáveis no texto.'
    },

    operators: {
      title: 'Operadores Matemáticos e de Comparação',
      theory: `**Operadores Matemáticos:**
• + (soma), - (subtração), * (multiplicação)
• / (divisão), // (divisão inteira), % (resto)
• ** (potenciação)

**Operadores de Comparação:**
• == (igual), != (diferente)
• > (maior), < (menor)
• >= (maior ou igual), <= (menor ou igual)`,
      code: `# Operações matemáticas
a = 10
b = 3

print(f"{a} + {b} = {a + b}")
print(f"{a} - {b} = {a - b}")
print(f"{a} * {b} = {a * b}")
print(f"{a} / {b} = {a / b}")
print(f"{a} // {b} = {a // b}")  # divisão inteira
print(f"{a} % {b} = {a % b}")    # resto da divisão
print(f"{a} ** {b} = {a ** b}")  # potenciação

# Comparações
print(f"{a} == {b}? {a == b}")
print(f"{a} > {b}? {a > b}")`,
      explanation: 'Os operadores // e % são muito úteis: // te dá a parte inteira da divisão, % te dá o resto.'
    },

    conditions: {
      title: 'If, Elif, Else',
      theory: `Estruturas condicionais permitem tomar decisões no código:

• **if**: executa se a condição for verdadeira
• **elif**: testa outra condição se a anterior foi falsa
• **else**: executa se nenhuma condição anterior foi verdadeira

⚠️ **Atenção à indentação!** Python usa espaços para definir blocos de código.`,
      code: `# Exemplo de estrutura condicional
nota = 8.5

if nota >= 9:
    print("Excelente! 🎉")
    status = "Aprovado com distinção"
elif nota >= 7:
    print("Muito bom! 👍")
    status = "Aprovado"
elif nota >= 5:
    print("Na média 😐")
    status = "Aprovado"
else:
    print("Precisa estudar mais 📚")
    status = "Reprovado"

print(f"Status final: {status}")

# Exemplo com múltiplas condições
idade = 20
tem_carteira = True

if idade >= 18 and tem_carteira:
    print("Pode dirigir!")
else:
    print("Não pode dirigir ainda.")`,
      explanation: 'Use and, or e not para combinar condições. Lembre-se: indentação (espaços) é obrigatória!'
    },

    loops: {
      title: 'Loops: For e While',
      theory: `Loops repetem código automaticamente:

**For**: quando você sabe quantas vezes repetir
**While**: quando você repete até uma condição mudar

**range()**: gera sequências de números
• range(5): 0, 1, 2, 3, 4
• range(2, 8): 2, 3, 4, 5, 6, 7
• range(0, 10, 2): 0, 2, 4, 6, 8`,
      code: `# Loop FOR - repetir número específico de vezes
print("Contando até 5:")
for i in range(1, 6):
    print(f"Número: {i}")

print("\\nTabuada do 3:")
for i in range(1, 11):
    resultado = 3 * i
    print(f"3 x {i} = {resultado}")

# Loop WHILE - repetir enquanto condição for verdadeira
print("\\nContagem regressiva:")
contador = 5
while contador > 0:
    print(f"{contador}...")
    contador -= 1  # mesmo que: contador = contador - 1
print("🚀 Decolagem!")

# For com strings
nome = "Python"
print(f"\\nLetras da palavra '{nome}':")
for letra in nome:
    print(f"-> {letra}")`,
      explanation: 'For é ideal para repetições definidas, while para repetições baseadas em condições. Cuidado com loops infinitos!'
    },

    functions: {
      title: 'Criando Funções',
      theory: `Funções são blocos de código reutilizáveis:

**Vantagens:**
• Evita repetição de código
• Organiza melhor o programa
• Facilita manutenção e testes

**Estrutura:**
def nome_funcao(parâmetros):
    # código da função
    return resultado  # opcional`,
      code: `# Função simples
def saudacao(nome):
    return f"Olá, {nome}! Bem-vindo!"

# Função com múltiplos parâmetros
def calcular_media(nota1, nota2, nota3):
    media = (nota1 + nota2 + nota3) / 3
    return round(media, 2)  # arredonda para 2 casas decimais

# Função com parâmetro padrão
def apresentar(nome, idade=18):
    return f"Eu sou {nome} e tenho {idade} anos."

# Testando as funções
print(saudacao("Maria"))
print(f"Média: {calcular_media(8.5, 7.0, 9.2)}")
print(apresentar("João"))
print(apresentar("Ana", 25))

# Função que não retorna valor (só executa ações)
def mostrar_info(nome, curso):
    print(f"Estudante: {nome}")
    print(f"Curso: {curso}")
    print("-" * 20)

mostrar_info("Carlos", "Python")`,
      explanation: 'Use return para enviar um resultado de volta. Parâmetros padrão tornam algumas informações opcionais.'
    },

    lists: {
      title: 'Trabalhando com Listas',
      theory: `Listas guardam múltiplos valores em ordem:

**Características:**
• Podem conter diferentes tipos de dados
• São mutáveis (podem ser modificadas)
• Começam no índice 0
• Suportam índices negativos (-1 = último item)`,
      code: `# Criando listas
frutas = ["maçã", "banana", "laranja", "uva"]
numeros = [1, 2, 3, 4, 5]
mista = ["João", 25, True, 1.75]

print("Lista de frutas:", frutas)
print("Primeira fruta:", frutas[0])
print("Última fruta:", frutas[-1])

# Adicionando itens
frutas.append("manga")  # adiciona no final
frutas.insert(1, "pêra")  # adiciona na posição 1
print("Após adicionar:", frutas)

# Removendo itens
frutas.remove("banana")  # remove por valor
fruta_removida = frutas.pop()  # remove e retorna o último
print(f"Removeu: {fruta_removida}")
print("Lista atual:", frutas)

# Operações úteis
print(f"Tamanho da lista: {len(frutas)}")
print(f"Tem maçã? {'maçã' in frutas}")

# Loop em lista
print("\\nFrutas disponíveis:")
for i, fruta in enumerate(frutas):
    print(f"{i+1}. {fruta}")`,
      explanation: 'enumerate() te dá tanto o índice quanto o valor. Muito útil para numerar itens!'
    },

    practice: {
      title: 'Vamos Praticar!',
      theory: `**Desafios para praticar:**

1. **Calculadora simples**: operações básicas
2. **Verificador de idade**: maior/menor de idade
3. **Lista de compras**: adicionar/remover itens
4. **Contador de palavras**: contar caracteres

💡 **Dica**: Comece simples e vá adicionando funcionalidades!`,
      code: `# Desafio 1: Calculadora simples
def calculadora():
    print("=== CALCULADORA SIMPLES ===")
    a = float(input("Digite o primeiro número: "))
    operacao = input("Digite a operação (+, -, *, /): ")
    b = float(input("Digite o segundo número: "))
    
    if operacao == '+':
        resultado = a + b
    elif operacao == '-':
        resultado = a - b
    elif operacao == '*':
        resultado = a * b
    elif operacao == '/' and b != 0:
        resultado = a / b
    else:
        return "Operação inválida ou divisão por zero!"
    
    return f"{a} {operacao} {b} = {resultado}"

# Desafio 2: Lista de compras
lista_compras = []

def adicionar_item(item):
    lista_compras.append(item)
    print(f"'{item}' adicionado à lista!")

def mostrar_lista():
    if lista_compras:
        print("\\n📝 Lista de Compras:")
        for i, item in enumerate(lista_compras, 1):
            print(f"{i}. {item}")
    else:
        print("Lista vazia!")

# Exemplo de uso
adicionar_item("Leite")
adicionar_item("Pão")
adicionar_item("Ovos")
mostrar_lista()

print("\\n🎯 Agora é sua vez de praticar!")`,
      explanation: 'Tente modificar esses exemplos! Adicione validações, novas funcionalidades ou crie seus próprios projetos.'
    }
  };

  const runCode = () => {
    setCodeOutput('Código executado! ✅\n(Num ambiente real, você veria o resultado aqui)');
    setCompletedSections(prev => new Set([...prev, activeSection]));
  };

  const currentContent = content[activeSection];
  const SectionIcon = sections.find(s => s.id === activeSection)?.icon || Code;

  return (
    <div className="max-w-6xl mx-auto p-6 bg-gradient-to-br from-blue-50 to-indigo-50 min-h-screen">
      <div className="text-center mb-8">
        <h1 className="text-4xl font-bold text-gray-800 mb-2">🐍 Python para Iniciantes</h1>
        <p className="text-gray-600">Aprenda programação de forma interativa e divertida!</p>
      </div>

      <div className="grid grid-cols-1 lg:grid-cols-4 gap-6">
        {/* Sidebar com navegação */}
        <div className="lg:col-span-1">
          <div className="bg-white rounded-lg shadow-lg p-4 sticky top-6">
            <h3 className="font-bold text-lg mb-4 text-gray-800">📚 Conteúdo</h3>
            <nav className="space-y-2">
              {sections.map((section) => {
                const Icon = section.icon;
                const isActive = activeSection === section.id;
                const isCompleted = completedSections.has(section.id);
                
                return (
                  <button
                    key={section.id}
                    onClick={() => setActiveSection(section.id)}
                    className={`w-full text-left p-3 rounded-lg transition-all flex items-center gap-3 ${
                      isActive 
                        ? 'bg-blue-100 text-blue-700 border-l-4 border-blue-500' 
                        : 'hover:bg-gray-50 text-gray-600'
                    }`}
                  >
                    <Icon className="w-4 h-4" />
                    <span className="flex-1 text-sm">{section.title}</span>
                    {isCompleted && <CheckCircle className="w-4 h-4 text-green-500" />}
                  </button>
                );
              })}
            </nav>
            
            <div className="mt-6 p-3 bg-green-50 rounded-lg">
              <div className="text-sm text-green-700">
                <strong>Progresso:</strong> {completedSections.size}/{sections.length}
              </div>
              <div className="w-full bg-green-200 rounded-full h-2 mt-2">
                <div 
                  className="bg-green-500 h-2 rounded-full transition-all"
                  style={{ width: `${(completedSections.size / sections.length) * 100}%` }}
                ></div>
              </div>
            </div>
          </div>
        </div>

        {/* Conteúdo principal */}
        <div className="lg:col-span-3 space-y-6">
          {/* Teoria */}
          <div className="bg-white rounded-lg shadow-lg p-6">
            <div className="flex items-center gap-3 mb-4">
              <SectionIcon className="w-6 h-6 text-blue-600" />
              <h2 className="text-2xl font-bold text-gray-800">{currentContent.title}</h2>
            </div>
            
            <div className="prose max-w-none">
              <div className="text-gray-700 whitespace-pre-line leading-relaxed">
                {currentContent.theory}
              </div>
            </div>
          </div>

          {/* Código */}
          <div className="bg-white rounded-lg shadow-lg p-6">
            <div className="flex items-center justify-between mb-4">
              <h3 className="text-lg font-semibold text-gray-800 flex items-center gap-2">
                <Code className="w-5 h-5" />
                Exemplo Prático
              </h3>
              <button
                onClick={runCode}
                className="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg flex items-center gap-2 transition-colors"
              >
                <Play className="w-4 h-4" />
                Executar
              </button>
            </div>
            
            <div className="bg-gray-900 text-green-400 p-4 rounded-lg font-mono text-sm overflow-x-auto">
              <pre>{currentContent.code}</pre>
            </div>
            
            {codeOutput && (
              <div className="mt-4 bg-gray-100 p-4 rounded-lg">
                <h4 className="font-semibold text-gray-700 mb-2">Saída:</h4>
                <pre className="text-sm text-gray-800">{codeOutput}</pre>
              </div>
            )}
          </div>

          {/* Explicação */}
          <div className="bg-yellow-50 border-l-4 border-yellow-400 p-4 rounded-lg">
            <div className="flex items-start gap-3">
              <div className="text-yellow-600 text-lg">💡</div>
              <div>
                <h4 className="font-semibold text-yellow-800 mb-1">Explicação:</h4>
                <p className="text-yellow-700">{currentContent.explanation}</p>
              </div>
            </div>
          </div>

          {/* Navegação */}
          <div className="flex justify-between items-center">
            <button
              onClick={() => {
                const currentIndex = sections.findIndex(s => s.id === activeSection);
                if (currentIndex > 0) {
                  setActiveSection(sections[currentIndex - 1].id);
                }
              }}
              disabled={sections.findIndex(s => s.id === activeSection) === 0}
              className="px-4 py-2 bg-gray-200 text-gray-600 rounded-lg disabled:opacity-50 disabled:cursor-not-allowed hover:bg-gray-300 transition-colors"
            >
              ← Anterior
            </button>

            <div className="text-gray-500 text-sm">
              {sections.findIndex(s => s.id === activeSection) + 1} de {sections.length}
            </div>

            <button
              onClick={() => {
                const currentIndex = sections.findIndex(s => s.id === activeSection);
                if (currentIndex < sections.length - 1) {
                  setActiveSection(sections[currentIndex + 1].id);
                }
              }}
              disabled={sections.findIndex(s => s.id === activeSection) === sections.length - 1}
              className="px-4 py-2 bg-blue-500 text-white rounded-lg disabled:opacity-50 disabled:cursor-not-allowed hover:bg-blue-600 transition-colors"
            >
              Próximo →
            </button>
          </div>
        </div>
      </div>
    </div>
  );
};

export default PythonBeginnerGuide;
