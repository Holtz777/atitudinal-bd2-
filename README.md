CREATE TABLE
  musicas (
    id BIGINT PRIMARY KEY GENERATED ALWAYS AS INDENTITY,
    caminho VARCHER(60) UNIQUE NOT NULL,
    titulo varchar(120) NOT NULL,
    duracao INT NOT NULL, --Em segundos
    data_postagem DATE NOT NULL,
    poster BYTEA NOT NULL,
    cantor_id BIGINT NOT NULL,
    compositor_id BIGINT NOT NULL,
    genero_id BIGINT NOT NULL,
    FOREIGN KEY (cantor_id) REFERENCES artistas_compositores (id),
    FOREIGN KEY (compositor_id) REFERENCES artistas_compositores (id)
  );

CREATE TABLE
  artistas_compositores (
    id BIGINT PRIMARY KEY GENERATED ALWAYS AS INDENTITY,
    nome VARCHAR(120) NOT NULL,
    data_nascimento DATE NOT NULL,
    data_falecimento DATE,
    tipo char(1) NOT NULL, -- A/C (Artista/Compositor)
    biografia text,
    musica_mais_conhecida varchar(120) NOT NULL
  );

CREATE TABLE
  usuarios (
    id BIGINT PRIMARY KEY GENERATED ALWAYS AS INDENTITY,
    email VARCHER(100) UNIQUE NOT NULL,
    senha VARCHAR(100) NOT NULL,
    nome_completo VARCHAR(200) NOT NULL,
    idade INT NOT NULL,
    generos_preferidos text,
    data_criacao_perfil DATE NOT NULL,
    ultimo_acesso_app DATE,
    celular VARCHAR(13),
    plano_id BIGINT UNIQUE NOT NULL
  );

INSERT INTO
  musicas (
    caminho,
    titulo,
    duracao,
    data_postagem,
    cantor_id,
    compositor_id,
    poster,
    genero_id
  )
VALUES
  (
    'musica1.mp3',
    'Música 1',
    240,
    '2023-11-14',
    1,
    1,
    'poster1.jpg',
    1
  ),
  (
    'musica2.mp3',
    'Música 2',
    300,
    '2023-11-15',
    2,
    2,
    'poster2.jpg',
    2
  ),
  (
    'musica3.mp3',
    'Música 3',
    180,
    '2023-11-16',
    1,
    2,
    'poster3.jpg',
    3
  );

INSERT INTO
  artistas_compositores (
    nome,
    data_nascimento,
    data_falecimento,
    tipo,
    biografia,
    musica_mais_conhecida
  )
VALUES
  (
    'Artista 1',
    '1980-01-01',
    null,
    'A',
    'Biografia do Artista 1',
    'Musica 1'
  ),
  (
    'Artista 2',
    '1985-05-05',
    null,
    'A',
    'Biografia do Artista 2',
    'Musica 2'
  ),
  (
    'Compositor 1',
    '1990-10-10',
    null,
    'C',
    'Biografia do Compositor 1',
    'Musica 3'
  );

INSERT INTO
  usuarios (
    email,
    senha,
    nome_completo,
    idade,
    generos_preferidos,
    data_criacao_perfil,
    ultimo_acesso_app,
    celular,
    plano_id
  )
VALUES
  (
    'usuario1@email.com',
    'senha123',
    'Usuario 1',
     25,
    'Pop, Rock',
    '2023-11-17',
    '2023-11-17',
    '11999999999',
     1
  ),
  (
    'usuario2@email.com',
    'senha1234',
    'Usuario 2',
     24,
    'Jazz, Blues',
    '2023-11-18',
    '2023-11-19',
    '11999999998',
     2
  ),
  (
    'usuario3@email.com',
    'senha12345',
    'Usuario 3',
     23,
    'Funk, Trap',
    '2023-11-19',
    '2023-11-20',
    '11999999997',
     3
  );
