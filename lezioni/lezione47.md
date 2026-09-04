# Cookies

I cookie sono piccoli dati associati a un dominio e inviati dal browser nelle richieste compatibili. Possono essere creati dal server con l'header `Set-Cookie` o, con limiti, da JavaScript.

```javascript
document.cookie = "preferenza=scuro; Max-Age=3600; Path=/; Secure; SameSite=Lax";
```

`HttpOnly` impedisce l'accesso da JavaScript e va usato per cookie di sessione quando possibile. `Secure` richiede HTTPS; `SameSite` limita l'invio cross-site.

Non salvare token sensibili in cookie accessibili da script senza una valutazione accurata del rischio XSS. Rispettare consenso e normativa quando i cookie non sono strettamente necessari.

## Riepilogo

I cookie sono adatti a stato piccolo inviato al server, non a un database client-side. Attributi di sicurezza e gestione del consenso sono parte dell'implementazione.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione46) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione48)
