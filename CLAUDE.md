# Emprega Campos

Site de vagas e currículos de Campos do Jordão. Gratuito para candidatos e empresas. Apoiadores pagam R$ 50,00/mês por destaque.
Responda e escreva sempre em português do Brasil.

## Estado atual
- `site/` é um site estático (HTML, CSS e JS puros, sem build). É o que sobe no Netlify agora e depois na Hostinger.
- `site/index.html`: Início, Vagas de emprego, Cadastrar meu currículo (chat), Divulgar vaga, Apoiadores.
- `site/admin.html`: editor em `/admin`. Login `admin` / `campos2026` só afasta curioso, NÃO é segurança (a senha fica no código). Os currículos que aparecem lá são de exemplo.
- Dados: `vagas.json`, `apoiadores.json` (logo em data URL), `numeros.json` (contador de currículos). O admin baixa o JSON novo e a pessoa envia para a hospedagem no lugar do antigo.
- Envios de empresas e candidatos hoje usam Netlify Forms (formulários ocultos `vaga` e `curriculo` no topo do `index.html`). Isso só funciona no Netlify.

## Marca
- Fundo cinza `#1a1a1a`, texto branco, verde `#6ab908` como destaque (botões, aba ativa, etiquetas).
- Logos: `simbolo.png` (aperto de mãos em setas) e `nome.png` ("emprega campos"). Prévia de link: `og.png`.
- Fontes: Outfit (títulos) e DM Sans (texto), pelo Google Fonts.

## Regras de produto
- Candidato: chat com nome, nascimento, WhatsApp, e-mail (opcional), escolaridade, cursos, Word, Excel, e-mails, CNH, área, experiência, turno, foto (câmera ou galeria, obrigatória). Depois resumo, confirmação e autorização LGPD. O currículo vira PNG que o candidato pode baixar.
- Empresa: divulga vaga sem login (empresa, vaga, contato, turno, descrição). A vaga fica "aguardando aprovação".
- Vaga some do site depois de 30 dias, ou quando marcada como preenchida. Pode ser renovada.
- Admin: vê currículos, sugere vagas e candidatos compatíveis (por área e turno), compartilha currículo em PNG com mensagem pronta por WhatsApp ou e-mail, aprova vagas, cadastra apoiadores.
- Apoiadores: texto fixo na página, botão "Assine já" abre o WhatsApp (12) 98153-3470 com mensagem pronta. Cada apoiador tem logo, contato e endereço. Sempre 6 espaços "Sua logo aqui" no mínimo.

## Pendente (ordem sugerida)
1. **Servidor com login.** Hoje não há como proteger currículos. Plano: contas de empresa com aprovação, currículo só visível depois de ter vaga aprovada, resumo primeiro e contato revelado ao toque, registro de quem viu o contato de quem, limite diário, termos de uso. Hospedagem na Hostinger: opção A (site na Hostinger + Supabase para login e banco, recomendada) ou B (PHP + MySQL no próprio plano, confirmar se o plano tem). Decidir: entrada por e-mail e senha ou por código no e-mail.
2. Trocar Netlify Forms e os arquivos JSON pelo banco quando o servidor existir. O admin passa a ler dados reais.
3. Política de privacidade, termos de uso e jeito de o candidato pedir exclusão do currículo (LGPD).
4. Domínio próprio. Depois colocar o endereço completo em `og:image` no `index.html` (o WhatsApp precisa de URL absoluta).
5. Avisos automáticos de vaga e currículo novos (e-mail ou WhatsApp).
6. Testar com cerca de 5 candidatos e 5 empresas reais da cidade.

## Cuidados
- Nunca guardar senha ou chave secreta no código do site. Chaves públicas (Supabase anon) podem ficar, desde que as regras de acesso do banco estejam certas.
- Os currículos têm dados pessoais (telefone, foto, nascimento). Tratar com LGPD em qualquer mudança.
- Testar sempre em tela de celular. A maioria dos usuários virá pelo WhatsApp.
