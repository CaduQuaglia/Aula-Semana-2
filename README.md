# Aula-Semana-2

CREATE TABLE alunos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  sobrenome TEXT NOT NULL,
  turma TEXT NOT NULL,
  curso TEXT NOT NULL,
  data_nascimento DATE
);

CREATE TABLE cursos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  duracao_anos INT
);

CREATE TABLE matriculas (
  id SERIAL PRIMARY KEY,
  aluno_id INT REFERENCES alunos(id) ON DELETE CASCADE,
  curso_id INT REFERENCES cursos(id) ON DELETE CASCADE,
  data_matricula DATE DEFAULT CURRENT_DATE
);

INSERT INTO alunos (nome, sobrenome, turma, curso, data_nascimento)
VALUES ('Rafael', 'Cabral', 'T15', 'Engenharia da Computacao', '2006-05-30'),
       ('Maria', 'Lima', 'T15', 'Engenharia de Software', '2005-11-02'),
       ('João', 'de Caprio', 'T15', 'Ciencia da Computacao', '2006-06-11'),
       ('Antonio', 'Cillo', 'T15', 'Engenharia da Computacao', '2007-07-04'),
       ('Carlos', 'Quaglia', 'T15', 'Engenharia de Software', '2005-05-07'),
       ('Emanuelly', 'Dias', 'T15', 'Engenharia de Software', '2006-02-13');

INSERT INTO cursos (nome, duracao_anos)
VALUES ('Engenharia de Software', 4),
       ('Engenharia da Computacao', 4),
       ('Ciencia da Computacao', 4);

INSERT INTO matriculas (aluno_id, curso_id)
VALUES (1, 2),
       (2, 1),
       (3, 3),
       (4, 2),
       (5, 1),
       (6, 1);

SELECT * FROM alunos;

SELECT * FROM cursos;

SELECT a.nome AS aluno, c.nome AS curso, m.data_matricula AS data
FROM matriculas m
JOIN alunos a ON m.aluno_id = a.id
JOIN cursos c ON m.curso_id = c.id;
