# Proof Key for Code Exchange (PKCE)

O PKCE (Proof Key for Code Exchange) é um protocolo de segurança utilizado para proteger o fluxo de autorização no OAuth 2.0, especialmente em aplicações móveis e ambientes de cliente público (como SPA - Single Page Applications).

## Contexto

- **OAuth 2.0**: É um protocolo de autorização que permite que um aplicativo solicite permissão para acessar os recursos em nome do usuário sem expor as credenciais do usuário diretamente. Ele é amplamente utilizado para integração de serviços de terceiros em aplicações.

- **Problema**: Em um fluxo de autorização padrão do OAuth (como o Authorization Code Grant), um cliente autenticado recebe um código de autorização após o usuário fazer login. Esse código é então trocado por um token de acesso. O problema é que, em um ambiente público (como um aplicativo móvel ou uma SPA), o código de autorização pode ser potencialmente interceptado por atacantes.

## Solução com PKCE

O PKCE é uma extensão do OAuth 2.0 que resolve esse problema. Ele adiciona um passo extra ao fluxo de autorização:

1. O aplicativo gera um código aleatório chamado Code Verifier, e calcula um valor chamado Code Challenge baseado nesse Code Verifier. O Code Challenge é enviado junto com a solicitação de autorização.

2. Quando o servidor de autorização responde, ele armazena o Code Challenge e, quando o cliente envia o código de autorização de volta, ele também deve enviar o Code Verifier original. O servidor então verifica se o Code Verifier corresponde ao Code Challenge armazenado. Isso garante que apenas o aplicativo que iniciou a solicitação de autorização pode trocar o código de autorização por um token.

Isso torna o fluxo mais seguro, especialmente em ambientes onde o cliente é público e o código de autorização pode ser interceptado.

## Como Usar

Para implementar o PKCE em sua aplicação, siga as diretrizes específicas para a sua plataforma ou biblioteca OAuth. Geralmente, as bibliotecas OAuth populares (como `oauthlib` para Python ou `Spring Security OAuth` para Java) já oferecem suporte para PKCE.

## Referências

- [RFC 7636 - Proof Key for Code Exchange (PKCE)](https://tools.ietf.org/html/rfc7636)

---

Este arquivo README.md oferece uma explicação detalhada do PKCE, incluindo o contexto, a solução que ele oferece e como implementá-lo em uma aplicação. Também inclui referências importantes para a especificação oficial do PKCE.

