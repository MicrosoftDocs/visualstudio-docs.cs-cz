---
title: Přihlášení k předplatným sady Visual Studio může selhat při použití aliasů | Dokumenty společnosti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: Přihlášení může selhat, pokud jsou použity aliasy nebo popisné názvy
ms.openlocfilehash: 0f5ed4fe67dbd863a7ba4c22f10946cbeb1c36b0
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509054"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Přihlášení k předplatným sady Visual Studio může selhat při použití aliasů
V závislosti na typu účtu použitého k přihlášení nemusí být dostupná [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)předplatná při přihlášení k aplikaci správně zobrazena. Jednou z možných příčin je použití "aliasy" nebo "popisné názvy" místo přihlašovací identity, ke kterému je přiřazeno předplatné. Tomu se říká "aliasing".

## <a name="what-is-aliasing"></a>Co je aliasing?
Termín "aliasování" označuje uživatele, kteří mají různé identity pro přihlášení k systému Windows (nebo službě Active Directory) a přístup k e-mailu.

Aliasing u sebe může narazit, pokud má společnost pro přihlášeníJohnD@contoso.comk adresáři službu Microsoft Online Service, napříkladJohn.Doe@contoso.com" ", ale uživatelé přistupují ke svým e-mailovým účtům pomocí aliasů nebo popisných názvů, například " . Ujistěte se, že vaši uživatelé používají "Přihlašovací e-mailovou adresu", jak je uvedeno na portálu pro správu na adrese https://manage.visualstudio.com pro přístup k jejich odběry. 

## <a name="what-are-the-potential-issues"></a>Jaké jsou potenciální problémy?

V závislosti na typu účtu odběratele se mohou vyskytnou jeden ze dvou problémů. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problém neshody pracovního nebo školního účtu 
Neshoda hlavního názvu uživatele může dojít, pokud společnost má nastavenslužbu Active Directory, kde UserPrincipalName (UPN) není stejný jako primární adresa SMTP. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Jak zjistit, zda je vaše přihlašovací adresa ovlivněna neshodou upn 

1. Přihlaste se pomocí https://my.visualstudio.com/subscriptions přihlašovací adresy uvedené v e-mailu o přiřazení předplatného.

2. Ověřte, zda přihlašovací e-mailová adresa uvedená v pravém horním rohu stránky odpovídá adrese, kterou jste použili k přihlášení.  Pokud tomu tak není, váš upn je neodpovídající a nebudete moci zobrazit vaše předplatné. 

> [!div class="mx-imgBorder"]
> ![Přihlásit se e-mailovou adresu](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>Jak opravit neshodu upn

1. Přístup k portálu pro správu správy sady Visual Studio[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. Vyhledejte odběratele s problémem neshody hlavního uživatele. (Funkce [Filtr](search-license.md) může usnadnit nalezení odběratele.)

3. Změna přihlašovací e-mailové adresy na hlavní číslo uživatele 

0. Uložení změn 

0. Informujte účastníka, aby se odhlásit z portálu odběratele a přístup znovu pomocí UPN 

### <a name="personal-account-aliasing-issue"></a>Problém s aliasováním osobního účtu

Osobní účty předplatného může také dojít k problémům, pokud e-mailová adresa použitá k přihlášení k portálu předplatných Sady Visual Studio neodpovídá e-mailové adrese přidružené k předplatnému. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Jak zjistit, zda je váš osobní účet předplatného ovlivněn problémem s aliasováním

1. Přihlásit se k[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Ověřte, zda přihlašovací e-mailová adresa uvedená v pravém horním rohu stránky odpovídá adrese, kterou jste použili k přihlášení.  Pokud se přihlašovací e-mailová adresa neshodne jako e-mailová adresa použitá pro přístup k webu, dojde ke konfliktu mezi vaším účtem a aliasem.

#### <a name="how-to-fix-an-alias-issue"></a>Jak opravit problém aliasu

Platforma Visual Studio upřednostňuje primární alias, aby zobrazovala podrobnosti o předplatném. 

1. Přejděte na **Odkaz Spravovat způsob přihlášení k Microsoftu**. Pokud se zobrazí výzva, přihlaste se ke svému účtu Microsoft. 

2. V části Aliasy účtu vyberte **Vytvořit primární** vedle e-mailové adresy použité k přiřazení předplatného. 

> [!div class="mx-imgBorder"]
> ![Nastavení primární e-mailové adresy](_img//aliasing/account-aliases.png)

3. Odhlášení z portálu předplatných sady Visual Studio (https://my.visualstudio.com) 

4. Přihlaste se zpět pomocí účtu, který slouží k přiřazení předplatného, který by měl být nyní nakonfigurován jako primární alias. 

## <a name="preventing-aliasing-issues"></a>Zabránění problémům se aliasy

Jako správce existují dvě možnosti, jak zajistit, aby vaši [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)odběratelé měli úspěšné přihlašovací prostředí na aplikaci .
- První možností (doporučeno) je využít účet adresáře jako přihlášení k portálu https://my.visualstudio.compředplatných sady Visual Studio na adrese .  
- Druhou možností (méně bezpečnou) je umožnit odběratelům přihlásit se pomocí jiné e-mailové adresy, než je jejich e-mailová adresa adresáře.

Obě tyto možnosti jsou konfigurovány na portálu pro správu provedením následujících kroků:  
1. Přihlásit se[https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Pokud měníte jednoho uživatele, vyberte tohoto uživatele v tabulce a kliknutím pravým tlačítkem myši jej upravte. Otevře se panel, kde můžete upravit přihlašovací e-mailovou adresu. Proveďte potřebné aktualizace v poli přihlašovací e-mailové adresy. Klikněte na uložit a změny se projeví.  

0. Pokud potřebujete provést tyto změny u velkého množství uživatelů, můžete využít funkci hromadných úprav. Další informace načtete v článku [Úpravy více odběratelů pomocí hromadné úpravy.](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit)

> [!NOTE]
> U individuálních i hromadných změn obdrží odběratelé e-mail s pokyny, že se změnila jejich přihlašovací e-mailová adresa a budou se muset přihlásit pomocí aktualizované e-mailové adresy. Je také důležité si uvědomit, že pokud účastník dříve aktivované výhody pod jinou přihlašovací adresu, bude muset pokračovat v používání jiné přihlašovací adresu pro přístup k nim.  

## <a name="see-also"></a>Viz také
- [Dokumentace sady Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace k Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoftu 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úpravy předplatných](edit-license.md)
- [Určení maximálního využití](maximum-usage.md)


