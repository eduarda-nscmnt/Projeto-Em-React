# Projeto-Em-React

App.jsx

import { useEffect, useState } from 'react'
import './App.css'

function App() {
  const [usuario, setUsuario] = useState(null)
  const [repositorios, setRepositorios] = useState([])

  useEffect(() => {
    fetch('https://api.github.com/users/eduarda-nscmnt')
      .then(resposta => resposta.json())
      .then(dados => {
        setUsuario(dados)
      })

    fetch('https://api.github.com/users/eduarda-nscmnt/repos')
      .then(resposta => resposta.json())
      .then(dados => {
        setRepositorios(dados)
      })
  }, [])

  return (
    <main>

      {/* PERFIL */}
      <section className="perfil">

        <div className="perfil-topo">

          <img
            src={usuario?.avatar_url}
            alt="Foto do perfil do GitHub"
            className="foto-perfil"
          />

          <div className="perfil-informacoes">

            <h1>Maria Eduarda P. do Nascimento</h1>

            <p className="usuario">
              @{usuario?.login}
            </p>

            <p className="bio">
              Desenvolvedora em formação
            </p>

            <div className="github-info">

              <div>
                <strong>{usuario?.public_repos}</strong>
                <span>Repositórios</span>
              </div>

              <div>
                <strong>{usuario?.followers}</strong>
                <span>Seguidores</span>
              </div>

            </div>

          </div>

        </div>

        <div className="formacao-resumo">

          <p>
            Técnico em Desenvolvimento de Sistemas
          </p>

          <p>
            ECIT Mestre Sivuca - Severino Dias de Oliveira
          </p>

          <span>
            2024 — 2026
          </span>

        </div>

      </section>


      {/* SOBRE MIM */}
      <section className="sobre">

        <div className="sobre-cabecalho">

          <button>Sobre mim</button>
          <button>Formação</button>
          <button>Tecnologias</button>
          <button>Objetivo</button>

        </div>

        <div className="sobre-conteudo">

          <div className="sobre-card">

            <h3>Sobre mim</h3>

            <p>
              Sou estudante de Desenvolvimento de Sistemas,
              interessada em tecnologia e desenvolvimento
              de software.
            </p>

          </div>


          <div className="sobre-card">

            <h3>Formação</h3>

            <p>
              Técnico em Desenvolvimento de Sistemas
            </p>

            <span>
              2024 — 2026
            </span>

          </div>


          <div className="sobre-card">

            <h3>Instituição</h3>

            <p>
              ECIT Mestre Sivuca - Severino Dias de Oliveira
            </p>

          </div>


          <div className="sobre-card">

            <h3>Tecnologias</h3>

            <div className="tecnologias">

              <span>HTML</span>
              <span>CSS</span>
              <span>JavaScript</span>
              <span>React</span>

            </div>

          </div>


          <div className="sobre-card objetivo">

            <h3>Objetivo profissional</h3>

            <p>
              Meu objetivo é atuar na área de desenvolvimento
              de software, aprimorar meus conhecimentos em
              tecnologia e futuramente cursar Análise e
              Desenvolvimento de Sistemas.
            </p>

          </div>

        </div>

      </section>


      {/* PROJETOS */}
      <section className="repositorios">

        <h2>Meus projetos</h2>

        <div className="lista-repositorios">

          {repositorios.slice(0, 2).map((repositorio) => (

            <div
              className="card-repositorio"
              key={repositorio.id}
            >

              <h3>
                {repositorio.name}
              </h3>

              <p>
                {repositorio.description ||
                  'Projeto desenvolvido durante minha jornada de aprendizado.'
                }
              </p>

              <a
                href={repositorio.html_url}
                target="_blank"
                rel="noreferrer"
              >
                Ver projeto
              </a>

            </div>

          ))}

        </div>

      </section>

    </main>
  )

App.css:

/* ================================
   CONFIGURAÇÃO GERAL
================================ */

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  min-height: 100vh;

  background: #09070d;
  color: white;

  font-family: Arial, Helvetica, sans-serif;
}

main {
  width: 100%;
  max-width: 1000px;

  margin: 0 auto;
  padding: 50px 30px;
}


/* ================================
   PERFIL
================================ */

.perfil {
  width: 100%;

  padding: 30px 0 40px;

  border-bottom: 1px solid #2a2035;
}

.perfil-topo {
  display: flex;
  align-items: center;

  gap: 60px;

  max-width: 800px;

  margin: 0 auto;
}


/* ================================
   FOTO
================================ */

.foto-perfil {
  width: 170px;
  height: 170px;

  object-fit: cover;

  border-radius: 50%;

  border: 3px solid #7c3aed;

  padding: 4px;

  background: #120d1c;

  box-shadow:
    0 0 20px rgba(124, 58, 237, 0.35);
}


/* ================================
   INFORMAÇÕES DO PERFIL
================================ */

.perfil-informacoes {
  flex: 1;

  text-align: left;
}

.perfil-informacoes h1 {
  color: #ffffff;

  font-size: 30px;

  margin-bottom: 8px;
}

.usuario {
  color: #a855f7;

  font-size: 15px;

  margin-bottom: 15px;
}

.bio {
  color: #b8a9c9;

  font-size: 16px;

  margin-bottom: 25px;
}


/* ================================
   INFORMAÇÕES DO GITHUB
================================ */

.github-info {
  display: flex;

  gap: 35px;
}

.github-info div {
  display: flex;
  align-items: center;

  gap: 7px;
}

.github-info strong {
  color: #ffffff;

  font-size: 18px;
}

.github-info span {
  color: #aaa0b5;

  font-size: 14px;
}


/* ================================
   FORMAÇÃO
================================ */

.formacao-resumo {
  max-width: 800px;

  margin: 35px auto 0;

  padding-top: 25px;

  border-top: 1px solid #2a2035;

  text-align: left;
}

.formacao-resumo p {
  color: #d8cce2;

  font-size: 15px;

  line-height: 1.6;

  margin-bottom: 5px;
}

.formacao-resumo span {
  color: #a855f7;

  font-size: 14px;
}


/* ================================
   MENU SOBRE MIM
================================ */

.sobre {
  width: 100%;

  margin: 45px auto 0;
}

.sobre-cabecalho {
  display: flex;

  justify-content: center;

  gap: 50px;

  padding: 18px 0;

  border-top: 1px solid #2a2035;
  border-bottom: 1px solid #2a2035;

  margin-bottom: 30px;
}

.sobre-cabecalho button {
  background: none;

  border: none;

  color: #9f91ad;

  font-size: 14px;

  font-weight: bold;

  cursor: pointer;

  padding: 8px 5px;

  transition: 0.3s;
}

.sobre-cabecalho button:hover {
  color: #c084fc;
}


/* ================================
   CARDS SOBRE MIM
================================ */

.sobre-conteudo {
  display: grid;

  grid-template-columns: repeat(2, 1fr);

  gap: 20px;
}

.sobre-card {
  padding: 25px;

  background: #120d1c;

  border: 1px solid #2f2140;

  border-radius: 15px;

  transition: 0.3s;
}

.sobre-card:hover {
  transform: translateY(-4px);

  border-color: #6d28d9;

  box-shadow:
    0 0 20px rgba(124, 58, 237, 0.15);
}

.sobre-card h3 {
  color: #c084fc;

  font-size: 18px;

  margin-bottom: 12px;
}

.sobre-card p {
  color: #aaa0b5;

  font-size: 15px;

  line-height: 1.6;
}

.sobre-card span {
  display: inline-block;

  margin-top: 10px;

  color: #a855f7;

  font-size: 14px;
}


/* ================================
   TECNOLOGIAS
================================ */

.tecnologias {
  display: flex;

  flex-wrap: wrap;

  gap: 10px;

  margin-top: 15px;
}

.tecnologias span {
  margin: 0;

  padding: 7px 13px;

  background: #21142f;

  border: 1px solid #5b21b6;

  border-radius: 20px;

  color: #c4b5fd;

  font-size: 13px;
}


/* ================================
   OBJETIVO
================================ */

.objetivo {
  grid-column: span 2;
}


/* ================================
   PROJETOS
================================ */

.repositorios {
  margin-top: 60px;

  padding-top: 40px;

  border-top: 1px solid #2a2035;
}

.repositorios h2 {
  color: #c084fc;

  text-align: center;

  font-size: 28px;

  margin-bottom: 30px;
}

.lista-repositorios {
  display: grid;

  grid-template-columns: repeat(2, 1fr);

  gap: 20px;
}

.card-repositorio {
  padding: 25px;

  background: #120d1c;

  border: 1px solid #2f2140;

  border-radius: 15px;

  transition: 0.3s;
}

.card-repositorio:hover {
  transform: translateY(-5px);

  border-color: #7c3aed;

  box-shadow:
    0 0 25px rgba(124, 58, 237, 0.2);
}

.card-repositorio h3 {
  color: #c084fc;

  font-size: 19px;

  margin-bottom: 12px;
}

.card-repositorio p {
  color: #aaa0b5;

  line-height: 1.6;

  margin-bottom: 20px;
}

.card-repositorio a {
  color: #a855f7;

  text-decoration: none;

  font-weight: bold;

  transition: 0.3s;
}

.card-repositorio a:hover {
  color: #d8b4fe;
}


/* ================================
   CELULAR
================================ */

@media (max-width: 700px) {

  main {
    padding: 30px 20px;
  }

  .perfil-topo {
    flex-direction: column;

    gap: 25px;

    text-align: center;
  }

  .perfil-informacoes {
    text-align: center;
  }

  .perfil-informacoes h1 {
    font-size: 25px;
  }

  .foto-perfil {
    width: 140px;
    height: 140px;
  }

  .github-info {
    justify-content: center;
  }

  .formacao-resumo {
    text-align: center;
  }

  .sobre-cabecalho {
    gap: 15px;

    overflow-x: auto;

    justify-content: flex-start;
  }

  .sobre-cabecalho button {
    white-space: nowrap;
  }

  .sobre-conteudo {
    grid-template-columns: 1fr;
  }

  .objetivo {
    grid-column: span 1;
  }

  .lista-repositorios {
    grid-template-columns: 1fr;
  }

}
}

export default App
