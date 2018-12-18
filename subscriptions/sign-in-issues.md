---
title: Potíže s přihlášením k předplatným sady Visual Studio | Dokumentace Microsoftu
author: evanwindom
ms.author: lank
manager: lank
ms.date: 11/07/2018
ms.topic: conceptual
description: Další informace o problémech, které mohou vzniknout při přihlašování k předplatná sady Visual Studio
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 0883e5228a44f0df80e9de912029e21545d5ec2a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810576"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Potíže s přihlášením k předplatným sady Visual Studio
Na používání vašeho předplatného sady Visual Studio, musíte nejdřív přihlásit.  V závislosti na vaše předplatné může nastavíte ho s účtem Microsoft (MSA) nebo identita Azure Active Directory (AAD).  Tento článek popisuje některé problémy, které můžete narazit při přihlašování k vašemu předplatnému.  

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Účty Microsoft (MSA) nelze vytvořit pomocí pracovní nebo školní e-mailové adresy

Schopnost vytvářet nové osobní účet Microsoft (MSA) pomocí pracovní nebo školní e-mailové adresy je již není povolena pokud e-mailová doména je nakonfigurovaná ve službě Azure AD. Co to znamená? Pokud vaše organizace používá Office 365 nebo jiné firemní služby od Microsoftu, které jsou závislé na službě Azure AD a přidání názvu domény do vašeho tenanta Azure AD, uživatelé už nebudou moct vytvořit nový osobní účet Microsoft pomocí e-mailovou adresu ve vaší doméně. 

### <a name="why-was-this-change-made"></a>Proč se tato změna provedena?

S osobní Account Microsoft pracovní adresu jako uživatelské jméno je problémy koncových uživatelů a podobně IT oddělením. Příklad: 
- Uživatelé možná myslíte, že svůj osobní účet Microsoft je kompatibilní se obchodní a, ve kterých se nacházejí dodržování předpisů při jejich uložení obchodní dokument na jejich OneDrive 
- Uživatelé, kteří obecně opustit organizaci ztratí přístup k jeho pracovní e-mailovou adresu. Kdy to dělají, se nebudou moct zpět do svůj osobní účet Microsoft v případě, že zapomenete své heslo. Druhou stranu je, že IT oddělení může obnovit své heslo a dostat do osobního účtu bývalé zaměstnance. 
- IT oddělení mají o vlastnictví účtu a zabezpečení. Ale uživatelé potřebují pouze k umožňujícím zpětnou transformaci kódu k jejich pracovní e-mailové adresy jednou a můžete přejmenovat svůj účet v každém okamžiku v budoucnu. 

Situace je zvláště matoucí pro uživatele, kteří mají dva účty pomocí stejné e-mailová adresa (jedna ve službě Azure AD a jeden účet Microsoft). 

### <a name="what-does-this-experience-look-like"></a>Jak vypadá toto prostředí?

Pokud se pokusíte zaregistrovat pro aplikaci Microsoft uživatelů s pracovním nebo školním e-mailovou adresu, zobrazí se následující zpráva. 

   > [!div class="mx-imgBorder"]
   > ![Nejde vytvořit účet pomocí pracovního e-mailu](_img/sign-in-issues/cannot-use-work-email.png)

Ale pokud se pokusíte zaregistrovat aplikaci Microsoft, který podporuje osobní, tak i pracovní nebo školní účty, zobrazí tato zpráva:

   > [!div class="mx-imgBorder"]
   > ![Podporované pracovních nebo školních účtů](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Jsou existující účty se to týká?
Registrace bloku je zde popsáno, pouze zabraňuje vytváření nových účtů. Nemá žádný vliv na uživatele, kteří už mají Account Microsoft pracovní nebo školní e-mailovou adresu. Pokud jste již v této situaci, provedli jsme to usnadňuje přejmenovat osobního účtu Microsoft. To [článek podpory](http://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) poskytuje jednoduché podrobné pokyny. Přejmenování svého osobního účtu Microsoft je změna uživatelské jméno a nemá vliv na váš pracovní e-mail nebo jak se přihlásíte k firemní služby, jako je Office 365. Je také nebude mít vliv na váš osobní obsah – pouze změní tak, jak k němu přihlásíte. Můžete použít jinou (osobní) e-mailovou adresu, získání nového @outlook.com e-mailová adresa od Microsoftu, nebo použít své telefonní číslo jako nové uživatelské jméno. 

> [!NOTE]
> Pokud vaše oddělení IT vytvářet osobní účet Microsoft s vaší pracovní nebo školní e-mailu, například pro přístup k Microsoft firemní služby Premier Support, jako je a potom komunikovat váš tým správu před přejmenováním vašeho účtu. 

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Odstraňuje se přihlašovací adresa mohou bránit v přístupu k předplatnému

Pokud odstraníte jednu nebo více identit (MSA nebo AAD) přidružených k vašemu předplatnému, informace z vašeho předplatitele včetně uživatelského jména a ID přihlášení může být vykreslován anonymní, čímž dojde ke ztrátě přístupu ke svému předplatnému. 

Aby se zabránilo dopad na vaše předplatné přístup, použijte některý z následujících postupů.  
- Nasazení – MSA nebo AAD – systém správy jedinou identitu, ale ne obojí.  
- Přidružte identity AAD a MSA prostřednictvím tenanta. 


## <a name="next-steps"></a>Další kroky
- Zjistěte, jak [propojení účtů MSA a AAD](/azure/active-directory/b2b/add-users-administrator) v AAD.
- Další informace o [anonymizace](anonymization.md). 
