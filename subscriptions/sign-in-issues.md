---
title: Problémy s přihlašováním k předplatným sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 02/19/2021
ms.topic: conceptual
description: Informace o problémech, které mohou nastat při přihlašování k předplatným sady Visual Studio
ms.openlocfilehash: 5735e0c4178e6866539fff2edac6155642a1ba73
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607194"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Problémy s přihlašováním k předplatným sady Visual Studio
Pokud chcete použít předplatné sady Visual Studio, musíte se nejdřív přihlásit.  V závislosti na vašem předplatném jste ho možná nastavili pomocí účet Microsoft (MSA) nebo identity Azure Active Directory (AAD).  Tento článek popisuje některé problémy, se kterými se můžete setkat při přihlašování ke svému předplatnému.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Účty Microsoft (MSA) se nedají vytvořit pomocí e-mailových adres pracovní/školní služby.
Možnost vytvoření nového osobního účtu Microsoft (MSA) pomocí e-mailové adresy na pracovní/školní už není povolená, když je e-mailová doména nakonfigurovaná ve službě Azure AD. Co to znamená? Pokud vaše organizace používá Microsoft 365 nebo jiné firemní služby od Microsoftu, které spoléhají na Azure AD, a pokud jste do svého tenanta Azure AD přidali název domény, uživatelé už nebudou moct vytvořit novou osobní účet Microsoft pomocí e-mailové adresy ve vaší doméně.

### <a name="why-was-this-change-made"></a>Proč byla tato změna provedena?
Osobní účet Microsoft s pracovní adresou jako uživatelským jménem je fraught s problémy pro koncové uživatele a oddělení IT. Například:
- Uživatelé se mohou domnívat, že jejich osobní účet Microsoft jsou kompatibilní s obchodním a že jsou v souladu s předpisy, když ukládají obchodní dokument na OneDrive.
- Uživatelé, kteří odejdou z organizace, obecně ztratí přístup ke své pracovní e-mailové adrese. Pokud k tomu dojde, nemusí být schopni se vrátit do osobních účet Microsoft, pokud si zapomenete heslo. Překlopení je, že jeho IT oddělení může resetovat svoje heslo a získat si ho do osobního účtu bývalých zaměstnanců.
- Oddělení IT mají falešnou představu o vlastnictví a zabezpečení účtů. Ale uživatelé potřebují jenom přesměrovat kód na svou pracovní e-mailovou adresu jenom jednou a kdykoli v budoucnu může přejmenovat svůj účet.

Tato situace je zvláště matoucí pro uživatele, kteří mají dva účty se stejnou e-mailovou adresou (jedna ve službě Azure AD & jednu účet Microsoft).

### <a name="what-does-this-experience-look-like"></a>Jak toto chování vypadá?
Pokud se pokusíte zaregistrovat aplikaci pro příjemce Microsoftu pomocí pracovní nebo školní e-mailové adresy, zobrazí se následující zpráva.

   > [!div class="mx-imgBorder"]
   > ![Nejde vytvořit účet s pracovním e-mailem.](_img/sign-in-issues/cannot-use-work-email.png "Zadejte uživatelské jméno a heslo pro vytvoření účtu.")

Pokud se ale pokusíte zaregistrovat aplikaci Microsoftu, která podporuje osobní a pracovní/školní účty, měla by se zobrazit tato zpráva:

   > [!div class="mx-imgBorder"]
   > ![Pracovní/školní účty podporovány](_img/sign-in-issues/existing-account.png "Nemůžete se zaregistrovat tady pomocí pracovní nebo školní e-mailové adresy...")

### <a name="are-existing-accounts-affected"></a>Ovlivnily se stávající účty?
Zde popsané blokování registrace zabrání pouze vytváření nových účtů. Nemá žádný vliv na uživatele, kteří už mají účet Microsoft s pracovní nebo školní e-mailovou adresou. Pokud už v této situaci jste, usnadnili jsme přejmenování osobního účet Microsoft. Tento [článek podpory](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) poskytuje jednoduché podrobné pokyny. Přejmenování osobních účet Microsoft znamená změnu uživatelského jména a nemá vliv na váš pracovní e-mail ani na způsob, jakým se přihlašujete k obchodním službám, jako je například Microsoft 365. Neovlivní to i vaše osobní věci – stačí změnit způsob, jakým se k němu přihlašujete. Můžete použít jinou (osobní) e-mailovou adresu, získat novou @outlook.com e-mailovou adresu od Microsoftu nebo použít telefonní číslo jako nové uživatelské jméno.

> [!NOTE]
> Pokud vaše IT oddělení požádalo o vytvoření osobní účet Microsoft s vaším pracovním nebo školním e-mailem, například pro přístup k firemním službám Microsoftu, jako je třeba Premier Support, se před přejmenováním účtu poraďte s týmem správce.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Odstranění přihlašovací adresy může zabránit přístupu k předplatnému.
Pokud odstraníte jednu nebo více identit (MSA nebo AAD) přidružených k vašemu předplatnému, informace o vašem předplatiteli, včetně vašeho uživatelského jména a přihlašovacího ID, mohou být vygenerovány anonymně, což vede ke ztrátě přístupu k vašemu předplatnému.

Abyste se vyhnuli dopadům na přístup k předplatnému, použijte jeden z těchto postupů.
- Nasaďte jeden systém pro správu identit – buď MSA, nebo AAD, ale ne obojí.
- Přidružte identity AAD a MSA prostřednictvím tenanta.

## <a name="signing-in-may-fail-when-using-aliases"></a>Přihlášení se nemusí zdařit při použití aliasů.
V závislosti na typu účtu použitého k přihlášení nemusí být dostupné odběry při přihlášení ke správnému zobrazení [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) . Jednou z možných příčin je použití "aliasů" nebo "popisných názvů" místo přihlašovací identity, ke které je předplatné přiřazeno. Tento název se nazývá "aliasing".

### <a name="what-is-aliasing"></a>Co je aliasing?
Pojem "aliasing" odkazuje na uživatele, kteří mají různé identity pro přihlášení k Windows (nebo službě Active Directory) a pro přístup k e-mailu.

Aliasing se může vyskytnout, když má společnost Microsoft Online Service pro své adresáře, například JohnD@contoso.com , ale uživatelé mají přístup k e-mailovým účtům pomocí aliasů nebo popisných názvů, jako je například John.Doe@contoso.com . Pro mnoho zákazníků, kteří spravují svá předplatná prostřednictvím služby Volume Licensing Service Center (VLSC), může dojít k neúspěšnému přihlášení, protože zadaná e-mailová adresa ( John.Doe@contoso.com ) se neshoduje s adresou adresáře ( JohnD@contoso.com ) požadovanou pro úspěšné ověření prostřednictvím možnosti pracovní nebo školní účet.

### <a name="what-options-do-i-have"></a>Jaké možnosti mám?
Z perspektivy předplatitele je důležité, abyste nejdřív spolupracovali se správcem a pochopili konfiguraci identity vaší společnosti. V případě potřeby může správce potřebovat aktualizovat nastavení účtu z portálu pro správu nebo může být nutné vytvořit účet Microsoft (MSA) pomocí firemní e-mailové adresy. Před provedením kroků při vytváření MSA můžete mluvit s vaším správcem ohledně všech zásad nebo problémů s provedením této akce.

## <a name="resources"></a>Zdroje informací
- Pomoc s prodejem, předplatnými, účty a fakturací za předplatná sady Visual Studio najdete v tématu [Podpora předplatných](https://aka.ms/vssubscriberhelp)sady Visual Studio. 

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace k Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Další kroky
- Přečtěte si, jak [propojit účty MSA a AAD](/azure/active-directory/b2b/add-users-administrator) v AAD.
- Přečtěte si další informace o [anonymitě](anonymization.md).