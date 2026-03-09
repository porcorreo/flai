# FLAI - Framework Local de AI: Sua Inteligência Artificial Privada para Desenvolvimento de Software
## 🌟 Introdução
FLAI (Framework Local de AI) é uma solução revolucionária que traz o poder da inteligência artificial diretamente para sua máquina local, eliminando a dependência de APIs externas e garantindo privacidade total. Desenvolvido especificamente para projetos Fleting (Python + Flet), o FLAI transforma a maneira como você desenvolve, analisa e refatora código.
## Por que FLAI?
- 🔒 100% Privado: Seus códigos nunca saem da sua máquina
- ⚡ Sem Latência: Execução local elimina delays de rede
- 💰 Zero Custos: Nenhuma assinatura ou créditos necessários
- 🔄 Offline: Funciona mesmo sem internet
## 🏗️ Arquitetura Técnica
Visão Geral do Sistema
```shell
┌─────────────────────────────────────────────┐
│ FLAI Architecture │
├─────────────────────────────────────────────┤
│ ┌────────────┐ ┌────────────┐ │
│ │ User │◄──►│ FLAI │ │
│ │ Interface │ │ Shell │ │
│ └────────────┘ └────────────┘ │
│ │ │ │
│ ▼ ▼ │
│ ┌────────────┐ ┌────────────┐ │
│ │ Fleting │ │ Ollama │ │
│ │ Project │ │ Manager │ │
│ └────────────┘ └────────────┘ │
│ │ │ │
│ └───────────────────┼──────────────-┘
│ ▼ │
│ ┌────────────┐ │
│ │ Local │ │
│ │ LLM │ │
│ │ (Phi-3) │ │
│ └────────────┘ │
└─────────────────────────────────────────────┘
```
## Componentes Principais
### 1. Ollama Manager
```py
class OllamaManager:
"""
Gerenciador inteligente que detecta e executa Ollama automaticamente
Funciona sem necessidade de configurar PATH do sistema
"""
- find_ollama(): Busca em múltiplos locais do sistema
- start_server(): Inicia servidor em background
- run_model(): Executa modelos via API local
- ensure_ready(): Prepara tudo automaticamente
```
### 2. Project Scanner
```py
def scan_project(project_root: Path) -> List[Dict]:
"""
Escaneia projetos Fleting com segurança
Acesso restrito apenas ao diretório do projeto
"""
- Analisa estrutura MVC
- Identifica arquivos Python e Flet
- Gera contexto para a IA
```
### 3. Security Sandbox
```python
class SecurityManager:
"""
Sandbox de segurança que restringe acesso
A IA só pode analisar arquivos do projeto atual
"""
- validate_path(): Valida se caminho está dentro do projeto
- sanitize_response(): Remove referências externas
- create_security_warning(): Gera avisos de segurança
```
### 🚀 Começando
Pré-requisitos
- Python 3.10+
- 8GB+ de RAM (recomendado)
- Windows, Linux ou macOS
Instalação Rápida
```bash
# 1. Clone o projeto ou use via pip
pip install fleting
# 2. Crie um projeto Fleting
fleting init meu_projeto
cd meu_projeto
# 3. Configure a IA local
python -m fleting.flai.cli init ia
# 4. Execute o shell interativo
python -m fleting.flai.cli shell
```
## Setup Automático
O FLAI detecta automaticamente:
✅ Presença do Ollama
✅ Modelos instalados
✅ Configurações do sistema
✅ Permissões de acesso
## 🛠️ Funcionalidades Principais
### 1. Análise de Projetos Inteligente
```bash
# Analise automaticamente sua estrutura MVC
FLAI> "Analise a arquitetura do meu projeto"
# Saída exemplo:
"""
📊 Análise do Projeto 'meu_projeto'
✅ Pontos Fortes:
• Estrutura MVC bem definida
• Separação clara entre camadas
• Views Flet organizadas
⚠️ Áreas de Melhoria:
• Controllers muito acoplados
• Falta service layer
• Testes unitários ausentes
🎯 Sugestões:
1. Criar app/services/ para lógica de negócio
2. Implementar repository pattern nos models
3. Adicionar testes unitários com pytest
"""
```
### 2. Code Review Automático
```python
# O FLAI analisa seu código em tempo real
FLAI> "Revise o arquivo app/controllers/user_controller.py"
# Identifica automaticamente:
# • Code smells
# • Violações de princípios SOLID
# • Oportunidades de refatoração
# • Boas práticas faltantes
```
### 3. Sugestões Contextuais
```python
FLAI> "Como implementar autenticação JWT?"
# Resposta baseada no SEU projeto:
"""
Baseado na sua estrutura atual, sugiro:
1. Criar app/auth/jwt_handler.py:
```python
import jwt
from datetime import datetime, timedelta
class JWTHandler:
def create_token(self, user_id: str) -> str:
payload = {
'user_id': user_id,
'exp': datetime.utcnow() + timedelta(hours=24)
}
return jwt.encode(payload, SECRET_KEY, algorithm='HS256')
Adicionar middleware de autenticação
Atualizar UserController para usar JWT
"""
```
### 4. **Checklist Automático**
O FLAI gera automaticamente um checklist baseado nas melhores práticas:
```py
"""
# Checklist do Projeto Fleting
## ✅ Estrutura MVC
- [x] Pasta app encontrada
- [ ] Separação clara entre UI e lógica
- [ ] Controllers finos e especializados
## ✅ Models
- [ ] Validações de dados implementadas
- [ ] Repositórios isolados da lógica de negócio
## ✅ Views (Flet)
- [ ] Componentes reutilizáveis
- [ ] Layouts responsivos
"""
```
## 🔧 Integração com Ollama
Modelos Suportados
O FLAI funciona com qualquer modelo Ollama, mas recomenda:
Modelo RAM Uso Recomendado
- Phi-3 Mini 8GB Análise rápida, projetos pequenos
- Llama 3.2 3B 8GB Código e arquitetura
- Code Llama 7B 16GB Projetos complexos
- Mistral 7B 16GB Texto geral e documentação
Instalação Automática de Modelos
```py
# O FLAI gerencia automaticamente os modelos
manager = OllamaManager()
manager.install_model("phi3:mini") # Baixa se necessário
manager.ensure_ready() # Prepara tudo
```
## 🎯 Casos de Uso
### 1. Desenvolvimento Guiado por IA
```python
# Descreva o que precisa e o FLAI sugere implementação
FLAI> "Preciso de um CRUD completo para Product"
"""
Sugestão baseada no seu padrão MVC:
1. app/models/product.py:
```python
class Product:
id: str
name: str
price: float
category: str
app/controllers/product_controller.py:
python
class ProductController:
def create(self, product_data: dict): ...
def list(self): ...
def update(self, product_id: str, updates: dict): ...
app/views/product_view.py:
python
class ProductView:
def show_list(self, products: list): ...
def show_form(self): ...
"""
```
### 2. **Refatoração Assistida**
```python
FLAI> "Como extrair esta lógica do controller para um service?"
"""
Passo a passo:
1. Crie app/services/product_service.py
2. Mova a lógica de validação e regras de negócio
3. Atualize o controller para chamar o service
4. Mantenha o controller apenas para HTTP e validações básicas
Exemplo de service:
```python
class ProductService:
def validate_product_data(self, data: dict) -> bool:
# Lógica de validação complexa
pass
def calculate_taxes(self, price: float) -> float:
# Regras de negócio
pass
"""
```
### 3. **Análise de Dependências**
```python
FLAI> "Analise as dependências e acoplamento"
"""
📊 Análise de Dependências:
• UserController → UserModel: ✅ OK
• ProductController → UserController: ⚠️ Acoplamento alto
• AuthService → Database: ✅ Interface bem definida
🔍 Recomendações:
1. Usar injeção de dependência
2. Criar interfaces para serviços
3. Implementar padrão repository
"""
```
## 🔒 Segurança e Privacidade
Sandbox de Segurança
```python
# O FLAI opera em sandbox restrita
class ProjectSandbox:
"""
Garante que a IA só acessa arquivos do projeto
"""
- Bloqueia acesso a sistema de arquivos
- Filtra referências externas
- Valida todos os caminhos
Nenhum Dado Externa
✅ Código nunca enviado para nuvem
✅ Análise 100% local
✅ Modelos baixados uma vez, usados offline
✅ Configurações salvas localmente
## 📊 Performance
Benchmarks
Operação Tempo Médio Notas
Inicialização 2-5 segundos Cache otimizado
Análise de projeto 1-3 segundos Scanner eficiente
Consulta ao modelo 2-10 segundos Depende do hardware
Processamento em lote Variável Paralelização disponível
Otimizações
python
# Cache inteligente
cache.set("project_analysis", result, ttl=300) # 5 minutos
cache.get("model_status") # Evita verificações repetidas
# Lazy loading
manager.ensure_ready(lazy=True) # Só prepara quando necessário
# Connection pooling
OllamaManager (Singleton) # Uma instância global
```
## 🚧 Roadmap
Versão Atual (1.0)
Análise básica de projetos
Integração com Ollama
Shell interativo
Sistema de segurança
## Próximas Versões
- RAG (Retrieval-Augmented Generation)
- Pesquisa semântica no código
- Perguntas específicas sobre implementações
- Referência a trechos de código
- Agentes Especializados
- Agente de arquitetura
- Agente de testes
- Agente de documentação
- Workflows Automatizados
- Refatoração guiada passo a passo
- Migração de padrões
- Geração de código
- Integrações Avançadas
- Git integration (análise de commits)
- CI/CD pipelines
- Monitoramento de qualidade
## 🐛 Solução de Problemas
Problemas Comuns e Soluções
### 1. Ollama não encontrado
```bash
# O FLAI detecta automaticamente
python -m fleting.flai.cli init ia
# Se não encontrar, mostra instruções claras
2. Modelo não responde
bash
# Verificação automática
FLAI testa conexão e sugere soluções:
1. ollama serve
2. ollama pull phi3:mini
3. Reinicie o terminal
3. Acesso negado
python
# Sandbox de segurança ativa
# Apenas arquivos do projeto são acessíveis
# Mensagem clara: "Acesso restrito ao projeto atual"
Logs e Diagnóstico
bash
# Modo verbose
python -m fleting.flai.cli shell --verbose
# Logs detalhados
DEBUG=1 python -m fleting.flai.cli shell
# Diagnóstico automático
python -m fleting.flai.utils.diagnostic
```
## 🤝 Contribuindo
O FLAI é open-source e aceita contribuições:
```bash
# 1. Fork o repositório
# 2. Crie uma branch
git checkout -b feature/nova-funcionalidade
# 3. Desenvolva e teste
# 4. Envie Pull Request
# Áreas que precisam de ajuda:
# • Integração com mais modelos
# • Suporte a outras linguagens
# • Melhorias de performance
# • Novos casos de uso
## Padrões de Código
```
```python
# Seguimos estritamente:
# - Type hints em todas as funções
# - Docstrings completas
# - Testes unitários
# - Tratamento de erros robusto
def process_project(project: Path) -> AnalysisResult:
"""
Processa um projeto e retorna análise.
Args:
project: Caminho do projeto
Returns:
Resultado da análise
Raises:
ProjectError: Se projeto inválido
"""
# Implementação
```
## 📚 Documentação Adicional
API Reference
```python
# Principais classes e métodos
class OllamaManager:
"""Gerencia ciclo de vida do Ollama"""
@staticmethod
def get_instance() -> "OllamaManager":
"""Padrão singleton"""
def run_query(self, model: str, prompt: str) -> str:
"""Executa consulta no modelo"""
class ProjectAnalyzer:
"""Analisa projetos Fleting"""
def scan(self, project_root: Path) -> ProjectScan:
"""Escaneia estrutura"""
def analyze_architecture(self) -> ArchitectureReport:
"""Analisa arquitetura MVC"""
```
## Exemplos Práticos
### Exemplo 1: Pipeline Completo
```python
# Pipeline de análise automatizada
from fleting.flai import FlaiPipeline
pipeline = FlaiPipeline(project_path="meu_projeto")
report = pipeline.run_full_analysis()
print(f"Pontuação: {report.score}/100")
print(f"Recomendações: {report.recommendations}")
Exemplo 2: Integração Customizada
python
# Use o FLAI em seus próprios scripts
from fleting.flai.utils.ollama_simple import OllamaSimple
from fleting.flai.utils.scanner import scan_project
# Análise programática
ollama = OllamaSimple()
project_files = scan_project(Path("."))
prompt = f"Analise: {project_files}"
response = ollama.run("phi3:mini", prompt)
```
## 🎉 Conclusão
O FLAI representa um avanço significativo no desenvolvimento assistido por IA, trazendo:
### ✅ Vantagens Principais
- Privacidade Total - Seu código, suas regras
- Custo Zero - Sem mensalidades ou créditos
- Velocidade - Processamento local instantâneo
- Customizável - Adapta-se ao seu fluxo de trabalho
- Confiável - Funciona offline quando necessário
## 🎯 Para Quem é o FLAI?
- sDesenvolvedores Python que querem IA privada
- sEquipes que precisam de análise de código consistente
- sEducadores que ensinam boas práticas de programação
- sEmpresas com restrições de segurança de dados
## 🚀 Comece Agora
```bash
# É rápido e fácil
pip install fleting
fleting init meu-projeto
cd meu-projeto
python -m fleting.flai.cli shell
# Experimente:
# "Analise minha estrutura MVC"
# "Sugira melhorias"
# "Revise este controller"
```
## 📞 Suporte e Comunidade
GitHub: github.com/fleting/flai
Documentação: docs.fleting.dev/flai
Issues: Reporte bugs e sugira features
# FLAI - Transformando desenvolvimento local com inteligência artificial privada, segura e poderosa. 🚀
"Seu código merece análise inteligente, não compartilhamento de dados."
Artigo atualizado em: janeiro 2026
Versão: FLAI 1.0
Licença: MIT
Autor: Comunidade Fleting