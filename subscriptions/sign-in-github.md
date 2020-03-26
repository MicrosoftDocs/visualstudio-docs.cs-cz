---
title: Přihlášení k předplatným Visual Studia pomocí účtu GitHub | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 03/09/2020
ms.topic: conceptual
description: Přečtěte si, jak se přihlásit k předplatnému Visual Studia pomocí účtu GitHub.
ms.openlocfilehash: 722eeae315a8b4a6bd93fb1048846b147b294afa
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233233"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>Přihlášení k předplatnému Sady Visual Studio pomocí účtu GitHub 

Postup přihlášení k předplatnému Sady Visual Studio závisí na druhu účtu, který používáte. Můžete například používat účet Microsoft (MSA) nebo e-mailovou adresu, kterou vám poskytl váš zaměstnavatel nebo škola. Od ledna 2019 se teď můžete k přihlášení k některým předplatným přihlásit taky pomocí svého účtu GitHub. 

Tento článek vám poskytne postup pro přihlášení pomocí účtu GitHub.

## <a name="signing-in-with-your-github-account"></a>Přihlášení pomocí účtu GitHub

Podpora identit GitHub umožňuje používat stávající účet GitHub jako přihlašovací údaje pro nový nebo stávající účet Microsoft a propojovat váš účet GitHub s vaším účtem Microsoft. 

Když se přihlásíte pomocí GitHubu, Microsoft zkontroluje, jestli se e-mailové adresy přidružené k vašemu účtu GitHubu shodují s existujícím osobním nebo podnikovým účtem Microsoft. Pokud se adresa shoduje s vaším podnikovým účtem, budete místo toho vyzváni k přihlášení k tomuto účtu. Pokud se adresa shoduje s osobním účtem, přidáme k tomuto osobnímu účtu váš účet GitHub jako způsob přihlášení.

Po propojení přihlašovacích údajů k účtu GitHub a Microsoft můžete toto jednotné přihlášení použít kdekoli, kde se dá použít osobní účet Microsoft, například na webech Azure, v aplikacích Office a xboxu. Tyto účty lze také použít pro přihlášení hosta služby Azure Active Directory jako účet Microsoft za předpokladu, že e-mailová adresa odpovídá e-mailové adrese na pozvánce.

> [!NOTE]
> Propojení identity GitHubu s účtem Microsoft neposkytuje Microsoftu přístup k žádnému kódu. Když aplikace jako Azure DevOps a Visual Studio vyžadují přístup k úložištím kódu, budete vyzváni k udělení konkrétního souhlasu pro tento přístup. 

### <a name="frequently-asked-questions"></a>Nejčastější dotazy
Následující časté dotazy se týkají otázek týkajících se použití přihlašovacích údajů účtu GitHub k přihlášení k předplatným sady Visual Studio.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>Otázka: Zapomněl jsem heslo GitHubu.  Jak se nyní dostanu ke svému účtu?
A: Svůj účet GitHub můžete obnovit tak, že přejdete na [Resetování hesla](https://github.com/password_reset). Nebo můžete obnovit svůj účet Microsoft propojený s GitHubu zadáním e-mailové adresy účtu GitHub na [stránce Obnovit svůj účet](https://account.live.com/password/reset).

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>Otázka: Smazal jsem svůj účet GitHub.  Jak se teď dostanu ke svému účtu Microsoft (MSA)?
A: Pokud nemáte žádné další přihlašovací údaje na msa (jako heslo, ověřovací aplikace nebo bezpečnostní klíč), můžete obnovit svůj účet Microsoft pomocí e-mailové adresy k němu připojené. Chcete-li začít, přejděte na [obnovit svůj účet](https://account.live.com/password/reset). Ke svému účtu budete muset přidat heslo, abychom věděli, jak vás později přihlásit. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>Otázka: Na přihlašovací stránce není žádná možnost "Přihlásit se pomocí GitHubu".  Jak se můžu přihlásit pomocí svých přihlašovacích údajů githubu?
A: Zadejte e-mailovou adresu účtu GitHub, kterou jste zvolili při vytváření účtu Microsoft propojeného s GitHubem. Vyhledáme vás a pošleme na GitHub pro přihlášení. Nebo pokud je na přihlašovací stránce odkaz možností přihlášení, použijte tlačítko **Přihlásit se pomocí GitHubu,** které se zobrazí po kliknutí na tento odkaz. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>Otázka: Pomocí GitHubu se k některým svým aplikacím a produktům nemůžu přihlásit.  Proč?
A: Ne všechny produkty společnosti Microsoft přístup k GitHub.com z jejich přihlašovací stránky – například xbox konzole. Místo toho, když zadáte e-mailovou adresu z propojeného účtu GitHub, pošleme na tuto adresu kód, abychom mohli ověřit, že jste to opravdu vy. Stále se přihlašujete ke stejnému účtu, pouze jinou metodou přihlášení. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>Otázka: Přidal jsem heslo k účtu Microsoft, který jsem propojil se svým účtem GitHub.  Způsobí to problém?
A: Vůbec ne. Tím se vaše heslo k GitHubu nezmění. budete mít jen jiný způsob, jak se přihlásit ke svému účtu Microsoft. Kdykoli se přihlásíte pomocí své e-mailové adresy, nabídneme vám možnost přihlásit se pomocí hesla k účtu Microsoft nebo se přihlásit na GitHub. Důrazně doporučujeme, abyste se v případě, že potřebujete přidat heslo, ujistili, že se liší od hesla pro váš účet GitHub.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>Otázka: Chci přidat aplikaci Authenticator k účtu, který jsem vytvořil pomocí GitHubu.  Mohu to udělat?
A: Žádný problém - stačí stáhnout aplikaci a přihlásit se pomocí své e-mailové adresy. Když se přihlásíte pomocí své e-mailové adresy, budete vyzváni k výběru [aplikace Authenticator](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) nebo GitHubu jako přihlašovacích údajů.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>Otázka: Povolil jsem dvoufaktorové ověřování na účtech GitHub i Microsoft (MSA), ale když se přihlásím ke svému MSA, stále se mě zobrazí možnost ověření dvakrát.  Proč?
A: Z důvodu bezpečnostních omezení, Microsoft počítá přihlášení pomocí GitHub jako jednofaktorové ověření, i když máte dvoustupňové ověření povoleno tam. Proto budete muset znovu ověřit pro svůj účet Microsoft. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>Otázka: Jak poznám, jestli jsou moje účty Microsoft a GitHub propojené?
A: Kdykoli se podepíšíte pomocí aliasu svého účtu (e-mailová adresa, telefonní číslo, jméno Skype), zobrazíme vám všechny způsoby přihlášení k vašemu účtu. Pokud tam GitHub nevidíte, ještě jste ho nenastavili.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>Otázka: Jak můžu zrušit propojení účtů Microsoft a GitHub? 
A: Přejděte na [kartu Zabezpečení](https://account.microsoft.com/security) account.microsoft.com a klikněte na **další možnosti zabezpečení** pro odpojení účtu GitHub. Odpojení mandatorního účtu GitHub jej odebere jako metodu přihlášení a odebere přístup ke všem úložištím GitHub u Visual Studia. Jiné produkty společnosti Microsoft mohly požádat o přístup k vašemu účtu GitHub samostatně, takže odebránípřístupu zde neodebere přístup ve všech produktech. Přejděte na stránku [oprávnění aplikace](https://github.com/settings/applications) ve svém profilu GitHubu a odvolejte souhlas z aplikací, které jsou zde uvedeny.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>Otázka: Snažím se použít svůj účet GitHub k přihlášení, ale zobrazí se výzva, že už mám identitu Microsoftu, kterou bych měl použít.  Co se děje?
Odpověď: Pokud máte e-mailovou adresu Služby Azure Active Directory na vašem účtu GitHub, to znamená, že už máte identitu Microsoftu, která může přistupovat k Azure a spouštět kanály CI pomocí kódu GitHubu. Pomocí tohoto účtu zajistíte, že vaše prostředky Azure a sestavení kanály zůstávají v rámci hranice vaší organizace. Pokud však děláte osobní práci, doporučujeme na svůj účet GitHub uvést osobní e-mailovou adresu, abyste k ní měli vždy přístup. Až to uděláte, zkuste se znovu přihlásit a po zobrazení výzvy k přihlášení k pracovnímu nebo školnímu účtu **zvolte Použít jinou e-mailovou adresu.** To vám umožní vytvořit nový účet Microsoft pomocí této osobní e-mailové adresy.

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Po úspěšném přihlášení k portálu předplatných doporučujeme navštívit https://my.visualstudio.com/benefits stránku Výhody a prozkoumat skvělé nástroje, služby a nabídky, které máte k dispozici.  
