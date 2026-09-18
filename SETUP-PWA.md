# 📱 Setup do PWA - Caderno Digital

## Arquivos Criados

1. **index.html** - App completo com microfone
2. **manifest.json** - Configuração do PWA atualizada
3. **service-worker.js** - Service worker melhorado v2
4. **icon-192.svg** - Ícone 192x192 em SVG
5. **icon-512.svg** - Ícone 512x512 em SVG
6. **icon-192-maskable.svg** - Ícone 192x192 maskable
7. **icon-512-maskable.svg** - Ícone 512x512 maskable

---

## Como Configurar

### Passo 1: Converter SVG para PNG

Os ícones estão em **SVG**. Você precisa converter para **PNG**:

#### Opção A: Online (recomendado - rápido)
1. Va para: https://cloudconvert.com/svg-to-png
2. Faça upload de cada arquivo `.svg`
3. Configure: **192x192** para os arquivos `192` e **512x512** para os `512`
4. Baixe como PNG

#### Opção B: No seu computador (se tiver ImageMagick)
```bash
magick icon-192.svg -resize 192x192 icon-192.png
magick icon-512.svg -resize 512x512 icon-512.png
magick icon-192-maskable.svg -resize 192x192 icon-192-maskable.png
magick icon-512-maskable.svg -resize 512x512 icon-512-maskable.png
```

#### Opção C: Online simples
1. https://www.online-convert.com/convert-to-png
2. Upload SVG → PNG → Download

---

### Passo 2: Enviar para GitHub

Todos os arquivos devem estar no repositório **raiz** (/):

```
caderno-digital/
├── index.html
├── manifest.json
├── service-worker.js
├── icon-192.png ⭐ (convertido)
├── icon-512.png ⭐ (convertido)
├── icon-192-maskable.png ⭐ (convertido)
└── icon-512-maskable.png ⭐ (convertido)
```

---

### Passo 3: Verificar no Navegador

1. Abra seu app: https://annemouraia.github.io/caderno-digital/
2. No Chrome/Edge: clique nos **3 pontinhos** → "Instalar app"
3. No Safari (iOS): clique no **compartilhar** → "Adicionar à tela inicial"
4. Pronto! Funciona como app nativo! 🚀

---

## Checklist de Instalação

- [ ] SVGs convertidos para PNG (4 arquivos)
- [ ] Todos os arquivos enviados ao GitHub
- [ ] `index.html` está como arquivo principal
- [ ] `manifest.json` está configurado
- [ ] `service-worker.js` está registrado
- [ ] App abre offline
- [ ] Microfone funciona
- [ ] Dados salvam no localStorage

---

## Troubleshooting

### App não instala?
- ✅ Verificar se todos os ícones estão no repositório
- ✅ Recarregar página (Ctrl+F5)
- ✅ Aguardar 5-10 minutos

### Service Worker com erro?
- ✅ Limpar cache do navegador
- ✅ Recarregar página
- ✅ Verificar console (F12 → Console)

### Ícones não aparecem?
- ✅ Verificar nomes dos arquivos (devem ser exatos)
- ✅ Verificar se PNGs estão no repositório
- ✅ Recarregar página com Ctrl+F5

---

## Próximos Passos

Quando estiver com a instalação funcionando, vamos conectar ao **Supabase** para sincronizar dados! 🌐

Quer ajuda com isso? Me avisa! 📋
