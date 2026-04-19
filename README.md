Raspunsuri intrebari

1. Daca logout-ul ar fi un link GET, orice site extern ar putea sa il acceseze si sa delogheze userul fara voia lui. Cu POST, trebuie sa vina din aplicatie.

2. PasswordSignInAsync lucreaza cu UserName, nu cu Email. Noi vrem login cu email, asa ca mai intai gasim userul dupa email , apoi autentificam cu username-ul lui. In Identity, UserName si Email sunt campuri separate.

3. Daca ascundem butoanele doar in View, un user poate accesa direct /Articles/Edit/5 din bara de adrese si edita articolul, chiar daca nu vede butonul, deci verificarea trebuie sa fie in controller. Daca punem doar [Authorize] fara sa ascundem in View, aplicatia e sigura dar userul vede butoane care ii dau erori. 

4. Middleware pipeline-ul e o serie de pasi prin care trece fiecare request HTTP. UseAuthentication() trebuie sa fie inainte de UseAuthorization() pentru ca autorizarea trebuie sa stie cine e userul, iar identitatea e stabilita la pasul de autentificare.

5. Fara Identity ar fi trebuit sa scriem manual: hash-uirea parolelor, verificarea lor la login, gestionarea cookie-urilor de sesiune, un sistem de roluri si lockout dupa prea multe parole gresite. Identity face toate astea deja si corect — implementate manual ar fi aparut probabil greseli de securitate.

6. Identity e legat de Entity Framework si baze de date relationale, schema de tabele e fixa si greu de schimbat. Pentru proiecte simple, Identity aduce multa complexitate si campuri inutile.
