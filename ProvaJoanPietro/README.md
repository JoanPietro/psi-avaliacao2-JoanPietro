1- tinha rotas nos arquivos e colocadas de forma errada no controller, servico estava sendo criada de forma errada na camada controller, blueprints estava sendo aplicado de maneira errada, e fora da aplicação, html estava sendo feito de forma errada, sem conexao com o auth e servicos e fpra do view


2- o model ficou no models.py e na pasta dos blueprints ficou os controllers
ex:
@app.route("/")
def index():
    q = request.args.get("q", "")
    if q:
        lista = [s for s in models.servicos if q.lower() in s["descricao"].lower()]
    else:
        lista = models.servicos
    return render_template("index.html", servicos=lista, q=q,
                           categorias=models.todas_categorias())

ex:
class Servico:
    def __init__(self, id, descricao, categoria):
        self.id = id
        self.descricao = descricao
        self.categoria = categoria

3- Porque eles nao estao com armonia com o auth e servicos, fazendo com oque o codigo nao fucione
ex:

        <a href="{{ url_for('servicos.index') }}">Início</a>
        <a href="{{ url_for('auth.logout') }}">Sair</a>