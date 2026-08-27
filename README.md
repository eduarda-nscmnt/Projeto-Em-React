# Projeto-Em-React
App.jsx:

import { useEffect, useState } from 'react'
import './App.css'

function App() {
  const [usuario, setUsuario] = useState(null)
  const [repositorios, setRepositorios] = useState([])

  useEffect(() => {
    // Busca os dados do perfil no GitHub
    fetch('https://api.github.com/users/eduarda-nscmnt')
      .then(resposta => resposta.json())
      .then(dados => {
        setUsuario(dados)
      })

    // Busca os repositórios do GitHub
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

            <h1>
              Maria Eduarda P. do Nascimento
            </h1>

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


        {/* FORMAÇÃO */}
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

        <h2>Sobre mim</h2>

        <div className="sobre-conteudo">

          <div className="sobre-card">
            <h3>Nome</h3>

            <p>
              Maria Eduarda P. do Nascimento
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
              Meu objetivo é atuar na área de desenvolvimento de software,
              aprimorar meus conhecimentos em tecnologia e futuramente
              cursar Análise e Desenvolvimento de Sistemas.
            </p>

          </div>

        </div>

      </section>


      {/* PROJETOS */}
      <section className="repositorios">

        <h2>Meus projetos</h2>

        <div className="lista-repositorios">

          {repositorios.map((repositorio) => (

            <div
              className="card-repositorio"
              key={repositorio.id}
            >

              <h3>
                {repositorio.name}
              </h3>

              <p>
                {repositorio.description ||
                  'Projeto desenvolvido durante minha jornada de aprendizado.'}
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

  
