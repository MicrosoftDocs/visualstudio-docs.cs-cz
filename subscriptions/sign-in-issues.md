---
title: Problémy s přihlášením k předplatným Sady Visual Studio | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/11/2020
ms.topic: conceptual
description: Informace o problémech, které mohou vzniknout při přihlášení k předplatným Sady Visual Studio
ms.openlocfilehash: 8175a1d8d2c79aecad25952eebdf734e0a9d29d2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509015"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problémy s přihlášením k předplatným Sady Visual Studio
Chcete-li používat předplatné sady Visual Studio, musíte se nejprve přihlásit.  V závislosti na předplatném jste ho mohli nastavit buď pomocí účtu Microsoft (MSA), nebo pomocí identity Azure Active Directory (AAD).  Tento článek popisuje některé problémy, se kterými se můžete setkat při přihlašování k předplatnému.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Účty Microsoft (MSA) nelze vytvořit pomocí pracovních a školních e-mailových adres.
Možnost vytvořit nový osobní účet Microsoft (MSA) pomocí pracovní/školní e-mailové adresy už není povolena, když je e-mailová doména nakonfigurovaná ve službě Azure AD. Co to znamená? Pokud vaše organizace používá Office 365 nebo jiné obchodní služby od Microsoftu, které jsou závislé na Azure AD, a pokud jste do klienta Azure AD přidali název domény, uživatelé už nebudou moct vytvářet nový osobní účet Microsoft pomocí e-mailové adresy ve vaší doméně.

### <a name="why-was-this-change-made"></a>Proč byla tato změna provedena?
Mít osobní účet Microsoft s pracovní adresou jako uživatelským jménem je plné problémů pro koncové uživatele i oddělení IT. Například:
- Uživatelé si mohou myslet, že jejich osobní účet Microsoft splňuje požadavky firmy a že jsou v souladu s předpisy, když si ukládají firemní dokument na OneDrive.
- Uživatelé, kteří opustí organizaci, obvykle ztratí přístup ke své pracovní e-mailové adrese. Pokud tak učiní, nemusí být moci zpět do svého osobního účtu Microsoft, pokud zapomene své heslo. Druhou stranou je, že jejich IT oddělení by mohlo resetovat své heslo a dostat se na osobní účet bývalých zaměstnanců.
- IT oddělení mají falešný smysl pro vlastnictví a zabezpečení účtu. Uživatelé však potřebují pouze jednou převést kód na svou pracovní e-mailovou adresu a mohou svůj účet kdykoli v budoucnu přejmenovat.

Situace je obzvláště matoucí pro uživatele, kteří mají dva účty se stejnou e-mailovou adresou (jeden ve službě Azure AD & jeden účet Microsoft).

### <a name="what-does-this-experience-look-like"></a>Jak tato zkušenost vypadá?
Pokud se pokusíte zaregistrovat spotřebitelskou aplikaci Microsoft s pracovní nebo školní e-mailovou adresou, zobrazí se níže uvedená zpráva.

   > [!div class="mx-imgBorder"]
   > ![Nelze vytvořit účet s pracovním e-mailem](_img/sign-in-issues/cannot-use-work-email.png)

Pokud se však pokusíte zaregistrovat aplikaci Microsoft, která podporuje osobní a pracovní/školní účty, měla by se zobrazit tato zpráva:

   > [!div class="mx-imgBorder"]
   > ![Podporované pracovní/školní účty](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Jsou ovlivněny stávající účty?
Blok registrace popsaný zde pouze zabraňuje vytváření nových účtů. Nemá žádný vliv na uživatele, kteří už mají účet Microsoft s pracovní/školní e-mailovou adresou. Pokud jste již v této situaci, jsme usnadnili přejmenování osobního účtu Microsoft. Tento [článek podpory](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) obsahuje jednoduché pokyny krok za krokem. Přejmenování osobního účtu Microsoft znamená změnu uživatelského jména a nemá vliv na pracovní e-mail ani na způsob přihlášení k firemním službám, jako je Office 365. Nemá to ani vliv na vaše osobní věci – jen to mění způsob, jakým se k němu přihlašujete. Můžete použít jinou (osobní) e-mailovou adresu, získat novou @outlook.com e-mailovou adresu od společnosti Microsoft nebo použít své telefonní číslo jako nové uživatelské jméno.

> [!NOTE]
> Pokud vás vaše ODDĚLENÍ IT požádalo o vytvoření osobního účtu Microsoft pomocí pracovního/školního e-mailu, například pro přístup ke službám Microsoft business, jako je Premier Support, promluvte si před přejmenováním účtu se svým týmem pro správu.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Odstranění přihlašovací adresy může znemožnit přístup k předplatnému
Pokud odstraníte jednu nebo více identit (MSA nebo AAD) přidružených k vašemu předplatnému, informace o odběrateli včetně vašeho uživatelského jména a přihlašovacího ID mohou být anonymizovány, což vede ke ztrátě přístupu k vašemu předplatnému.

Chcete-li se vyhnout dopadům na přístup k předplatnému, použijte jednu z těchto technik.
- Nasazení jednoho systému správy identit – buď MSA nebo AAD – ale ne obojí.
- Přidružte identity AAD a MSA prostřednictvím klienta.

## <a name="signing-in-may-fail-when-using-aliases"></a>Při přihlašování se může selhat při použití aliasů.
V závislosti na typu účtu použitého k přihlášení nemusí být dostupná [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)předplatná při přihlášení k aplikaci správně zobrazena. Jednou z možných příčin je použití "aliasy" nebo "popisné názvy" místo přihlašovací identity, ke kterému je přiřazeno předplatné. Tomu se říká "aliasing".

### <a name="what-is-aliasing"></a>Co je aliasing?
Termín "aliasování" označuje uživatele, kteří mají různé identity pro přihlášení k systému Windows (nebo službě Active Directory) a přístup k e-mailu.

Aliasing může dojít, když společnost má Službu Microsoft Online pro JohnD@contoso.comjejich přihlášení k adresáři, jako je , John.Doe@contoso.comale uživatelé přístup k jejich e-mailové účty pomocí aliasů nebo popisné názvy, například . Pro mnoho zákazníků, kteří spravují svá předplatná prostřednictvím Centra multilicenčních služeb (VLSC), toJohn.Doe@contoso.commůže mít za následekJohnD@contoso.comneúspěšné přihlašovací prostředí, protože zadaná e-mailová adresa ( ) neodpovídá adrese adresáře ( ) požadované pro úspěšné ověření prostřednictvím možnosti "Pracovní nebo školní účet".

### <a name="what-options-do-i-have"></a>Jaké mám možnosti?
Z hlediska odběratele je důležité nejprve spolupracovat se správcem, abyste porozuměli konfiguraci identity vaší společnosti. V případě potřeby může být nutné, aby správce aktualizoval nastavení účtu z portálu pro správu nebo si můžete vytvořit účet Microsoft (MSA) pomocí firemní e-mailové adresy. Než podniknete kroky k vytvoření msa, promluvte si se správcem o všech zásadách nebo problémech s touto akcí. 

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Přečtěte si, jak [propojit účty MSA a AAD](/azure/active-directory/b2b/add-users-administrator) v rámci ad.
- Další informace o [anonymizaci](anonymization.md).
