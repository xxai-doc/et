<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Soovitatav on pärast kataloogi sisenemist esmalt installida nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) ja seejärel `direnv allow` ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) käivitatakse automaatselt pärast kataloogi sisenemist).

Tähendus on: hiina tõlge jaapani, korea, inglise keelde, ingliskeelne tõlge kõikidesse teistesse keeltesse. Kui soovite toetada ainult hiina ja inglise keelt, võite lihtsalt kirjutada `zh: en` .

Tähendus on: hiina tõlge jaapani, korea, inglise keelde, ingliskeelne tõlge kõikidesse teistesse keeltesse. Kui soovite toetada ainult hiina ja inglise keelt, võite lihtsalt kirjutada `zh: en` .

* [esiotsa kood](https://github.com/xxai-art/web)
* [Keelepaketid saidi kui terviku jaoks](https://github.com/xxai-art/web/tree/main/i18n)
* [Sisselogimismoodulite keelepaketid](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Veebisaidi mitmekeelne dokumentatsioon](https://github.com/xxai-doc)

Esiotsa programmeerimiskeel on [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , mis lisab mõned funktsioonid, mis põhinevad coffeescripti süntaksil, vt [./coffee_plus.md](./coffee_plus.md) .

## Veebilehtede ja dokumentide rahvusvahelistumine

Toetuge järgmisele kolmele projektile

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Järelliide on `.mdt` , saate kasutada süntaksit, mis sarnaneb süntaksiga `<+ ./coffee_plus/import.js>` , et viidata välistele failidele ja genereerida allahindlust järelliitega `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown-tõlge ei tõlgi koode ega linke ning salvestab tõlgitud laused vahemällu. Kui tõlget muudetakse, kuid originaalteksti ei muudeta, ei kirjuta selle uuesti täitmine tõlke muudatust üle.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Keelefailid `yaml` loodud veebisaitide tõlkimiseks.

### Dokumentide tõlkimise automatiseerimise juhised

Vaadake koodihoidlat [xxai-art/doc](https://github.com/xxai-art/doc)

Soovitatav on pärast kataloogi sisenemist esmalt installida nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) ja seejärel `direnv allow` ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) käivitatakse automaatselt pärast kataloogi sisenemist).

Et vältida suurt koodibaasi tõlgimist sadadesse keeltesse, lõin iga keele jaoks eraldi koodibaasi ja lõin organisatsiooni koodibaasi salvestamiseks

Keskkonnamuutuja `GITHUB_ACCESS_TOKEN` määramisel ja seejärel [faili create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) käivitamisel luuakse automaatselt koodihoidla.

Muidugi saab selle panna ka koodibaasi.

Tõlkeskripti viide [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Skripti koodi tõlgendatakse järgmiselt:

[bunx](https://bun.sh/docs/cli/bunx) asendab npx-i, mis on kiirem. Muidugi, kui sul pole bun installitud, võid selle asemel kasutada `npx` .

`bunx mdt zh` renderdab faili `.mdt` zh kataloogis kujul `.md` , vaadake allpool kahte lingitud faili

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` on tõlkimise põhikood (kui teil on installitud ainult `nodejs` , kuid `bun` ja `direnv` pole installitud, saate tõlkimiseks käivitada ka `npx i18n` ).

See parsib [faili i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , faili `i18n.yml` konfiguratsioon selles dokumendis on järgmine:

```
en:
zh: ja ko en
```

Tähendus on: hiina tõlge jaapani, korea, inglise keelde, ingliskeelne tõlge kõikidesse teistesse keeltesse. Kui soovite toetada ainult hiina ja inglise keelt, võite lihtsalt kirjutada `zh: en` .

Viimane on [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , mis eraldab sisu iga keele `README.md` põhipealkirja ja esimese alapealkirja vahel, et luua kirje `README.md` . Kood on väga lihtne, saate seda ise vaadata.

Tasuta tõlkimiseks kasutatakse Google API-t. Kui te ei pääse Google'ile juurde, konfigureerige ja määrake puhverserver, näiteks:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Tõlkeskript loob tõlgitud vahemälu `.i18n` kataloogis. Kontrollige seda `git status` ja lisage see koodihoidlasse, et vältida korduvaid tõlkeid.

Käivitage `bunx i18n` iga kord, kui muudate vahemälu värskendamiseks tõlget.

Kui originaalteksti ja tõlget muudetakse samal ajal, läheb vahemälu segamini, nii et kui soovite muuta, saate muuta ainult ühte ja seejärel käivitada vahemälu värskendamiseks `bunx i18n` .
