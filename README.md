<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Osa veebisaidi koodist on avatud lähtekoodiga, teretulnud aitama tõlget optimeerida.

## esiotsa kood

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
