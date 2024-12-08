CRUD com Firebase Firestore 🔥📊

Este projeto é uma aplicação CRUD simples para gerenciar usuários, utilizando o Firebase Firestore para armazenar dados. É possível adicionar, editar, excluir e visualizar usuários com nome, idade e cidade.

Funcionalidades ⚙️
Adicionar Usuário 👤
Editar Usuário ✏️
Excluir Usuário ❌
Histórico de alterações (criação, atualização, exclusão) 📜

🔧 Configuração do Firebase

Passo 1: Criar um projeto no Firebase 🚀
Acesse o Firebase Console.
Clique em Adicionar Projeto e siga as etapas para criar um novo projeto.

Passo 2: Criar um app Web no Firebase 🌐
No painel do seu projeto no Firebase, clique em Adicionar App e escolha a opção Web.
Siga as instruções para registrar o app. Após isso, o Firebase fornecerá um código de configuração que será necessário para a integração com o seu código. Este código será algo semelhante a:

const firebaseConfig = {
  apiKey: "API_KEY",
  authDomain: "PROJECT_ID.firebaseapp.com",
  projectId: "PROJECT_ID",
  storageBucket: "PROJECT_ID.appspot.com",
  messagingSenderId: "SENDER_ID",
  appId: "APP_ID",
  measurementId: "G-MEASUREMENT_ID"
};

Substitua o conteúdo do código de configuração no seu arquivo index.html com as informações fornecidas pelo Firebase.

Passo 3: Alterar as regras de segurança do Firestore 🔐
Acesse o Firestore no seu Firebase Console.
No painel esquerdo, clique em Regras.
Atualize as regras de segurança para permitir leitura e escrita sem autenticação (caso seu projeto não precise de autenticação por enquanto). Exemplo de regras básicas:

service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true; // Permitir leitura e escrita para todos
    }
  }
}

Essas regras são muito permissivas e servem para fins de desenvolvimento. Não utilize estas regras em produção. Para produção, é recomendado implementar regras mais seguras baseadas em autenticação e permissões.

🚀 Como Rodar o Projeto Localmente

Clone este repositório:

git clone https://github.com/SEU_USUARIO/CRUD-Firebase.git

Abra o arquivo index.html em um navegador: Não é necessário instalar nada além de um navegador. O Firebase será carregado automaticamente a partir da CDN.

💡 Como Funciona

Adicionar Usuário: Preencha os campos de nome, idade e cidade e clique em "Adicionar". O usuário será salvo no Firestore.
Editar Usuário: Clique em "Editar" ao lado de um usuário na lista para alterar seus dados.
Excluir Usuário: Clique em "Excluir" para marcar o usuário como excluído, sem removê-lo permanentemente do banco de dados.

🌐 Tecnologias Utilizadas

Firebase Firestore: Banco de dados NoSQL em tempo real.
HTML/CSS: Estrutura e estilo da página.
JavaScript: Lógica para manipulação dos dados no Firestore.

🎨 Estilos

O design da página utiliza uma combinação de um fundo escuro, bordas arredondadas e efeitos suaves para proporcionar uma experiência moderna e fluída.

🔑 Regras de Segurança

Atenção! As regras de segurança fornecidas aqui são apenas para fins de desenvolvimento e não são recomendadas para produção. Em um ambiente de produção, recomenda-se configurar regras adequadas para autenticação e autorização, garantindo que apenas usuários autenticados possam adicionar ou modificar dados.

Exemplo de regras de segurança para autenticação:

service cloud.firestore {
  match /databases/{database}/documents {
    match /usuarios/{userId} {
      allow read: if request.auth != null; // Usuários autenticados podem ler
      allow write: if request.auth != null && request.auth.uid == userId; // Apenas o usuário autenticado pode escrever seus próprios dados
    }
  }
}

📚 Referências

Documentação do Firebase Firestore
Regras de Segurança do Firestore

📝 Licença

Este projeto é proprietário e todos os direitos são reservados aos autores: Ana Karoline e Lucas Pereira.
