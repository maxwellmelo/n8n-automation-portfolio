# Como Ativar GitHub Pages

## Passo a Passo Rápido

1. **Acesse seu repositório no GitHub:**
   https://github.com/maxwellmelo/n8n-automation-portfolio

2. **Clique em "Settings" (Configurações)**
   - Está no menu superior do repositório

3. **No menu lateral esquerdo, clique em "Pages"**
   - Está na seção "Code and automation"

4. **Configure a fonte (Source):**
   - Em "Build and deployment"
   - Seção "Branch"
   - Selecione: **master**
   - Folder: **/ (root)**
   - Clique em **Save**

5. **Aguarde o deploy (1-3 minutos)**
   - Uma mensagem aparecerá: "Your site is ready to be published at..."
   - Quando estiver pronto, a mensagem mudará para: "Your site is live at..."

6. **Acesse seu site:**
   https://maxwellmelo.github.io/n8n-automation-portfolio/

## Verificação

Após alguns minutos, você poderá:
- Acessar a URL do GitHub Pages
- Ver todas as páginas funcionando
- Testar a navegação entre seções
- Verificar a responsividade em mobile

## Possíveis Problemas e Soluções

### Problema: "404 - File not found"
**Solução:** Aguarde mais alguns minutos. O primeiro deploy pode levar até 10 minutos.

### Problema: CSS não carrega corretamente
**Solução:** Verifique se os caminhos nos arquivos HTML estão relativos (sem `/` no início).
Já está correto: `css/style.css` ✓
Incorreto seria: `/css/style.css` ✗

### Problema: Links quebrados
**Solução:** Todos os links foram configurados como relativos, então devem funcionar.

## Domínio Customizado (Opcional)

Se você quiser usar um domínio próprio (ex: portfolio.seudominio.com):

1. Compre um domínio em um registrador (GoDaddy, Namecheap, etc.)
2. Configure DNS do domínio:
   - Tipo: CNAME
   - Name: portfolio (ou www)
   - Value: maxwellmelo.github.io
3. No GitHub Pages Settings, adicione seu domínio customizado
4. Aguarde propagação DNS (pode levar 24-48h)

## Monitoramento

### GitHub Actions
- Cada push no branch master dispara um rebuild automático
- Acesse "Actions" no repositório para ver o status dos deploys

### Analytics (Recomendado)
Adicione Google Analytics para monitorar:
1. Número de visitantes
2. Páginas mais acessadas
3. Tempo médio no site
4. Taxa de rejeição

## Atualizações Futuras

Para atualizar o site:

```bash
# 1. Faça suas modificações nos arquivos
# 2. Commit e push
cd E:\n8n-portifolio
git add .
git commit -m "Descrição das mudanças"
git push

# O site será atualizado automaticamente em 1-2 minutos
```

## URLs Importantes

- **Repositório:** https://github.com/maxwellmelo/n8n-automation-portfolio
- **Site ao vivo:** https://maxwellmelo.github.io/n8n-automation-portfolio/
- **Settings Pages:** https://github.com/maxwellmelo/n8n-automation-portfolio/settings/pages
- **Actions (Deploys):** https://github.com/maxwellmelo/n8n-automation-portfolio/actions

## Checklist Pós-Publicação

- [ ] Site acessível via URL do GitHub Pages
- [ ] Todas as páginas carregam corretamente
- [ ] CSS e JavaScript funcionando
- [ ] Links de navegação funcionais
- [ ] Responsivo em mobile
- [ ] Imagens carregando (se houver)
- [ ] Links de contato corretos
- [ ] Links sociais funcionando

## Compartilhamento

Após o site estar no ar, compartilhe em:
- LinkedIn
- Twitter
- Comunidades de n8n
- Grupos de automação
- Portfolio pessoal

---

**Desenvolvido por Maxwell Melo | 2024**
