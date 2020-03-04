---
title: Přihlášení k předplatným sady Visual Studio může při použití aliasů selhat. | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Přihlášení se nemusí zdařit, pokud se používají aliasy nebo popisné názvy.
ms.openlocfilehash: 824d24979d029d4a2de611db092afdbe908f64ea
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235123"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Přihlášení k předplatným sady Visual Studio může při použití aliasů selhat.
V závislosti na typu účtu použitého k přihlášení se nemusí při přihlašování k [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)správně zobrazit dostupná předplatná. Jednou z možných příčin je použití "aliasů" nebo "popisných názvů" místo přihlašovací identity, ke které je předplatné přiřazeno. Tento název se nazývá "aliasing".

## <a name="what-is-aliasing"></a>Co je aliasing?
Pojem "aliasing" odkazuje na uživatele, kteří mají různé identity pro přihlášení k Windows (nebo službě Active Directory) a pro přístup k e-mailu.

Aliasing se dá využít, když má společnost Microsoft Online Service pro své adresáře, jako je napříkladJohnD@contoso.com, ale uživatelé mají přístup k e-mailovým účtům pomocí aliasů nebo popisných názvů, jako je například "John.Doe@contoso.com". Pro mnoho zákazníků, kteří spravují svá předplatná prostřednictvím služby Volume Licensing Service Center (VLSC), může dojít k neúspěšnému přihlášení, protože zadaná e-mailová adresa ('John.Doe@contoso.com') neodpovídá adrese adresáře ('JohnD@contoso.com') požadované pro úspěšné ověření prostřednictvím možnosti pracovní nebo školní účet.  Zajistěte, aby vaši uživatelé používali e-mailovou adresu pro přihlášení, jak je uvedeno na portálu pro správu na https://manage.visualstudio.com pro přístup ke svým předplatným. 

## <a name="what-are-the-potential-issues"></a>Jaké jsou potenciální problémy?

V závislosti na typu účtu předplatitele se můžou setkat s jedním ze dvou problémů. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problém s neshodou uživatelského jména v pracovním nebo školním účtu 
Neshoda hlavního názvu uživatele (UPN) se může vyskytnout, když má společnost nastavenou službu Active Directory, kde název UserPrincipalName (UPN) není stejný jako primární adresa SMTP. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Jak zjistit, jestli je vaše přihlašovací adresa ovlivněná neshodou hlavního názvu uživatele (UPN) 

1. Přihlaste se https://my.visualstudio.com/subscriptions pomocí přihlašovací adresy uvedené v e-mailu s přiřazením předplatného.

2. Ověřte, že e-mailová adresa pro přihlášení uvedená v pravém horním rohu stránky odpovídá adrese, kterou jste použili k přihlášení.  Pokud tomu tak není, váš hlavní název uživatele se neshoduje a nebudete moct zobrazit vaše předplatné. 

> [!div class="mx-imgBorder"]
> e-mailová adresa ![přihlášení](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>Jak opravit hlavní název uživatele (UPN)

1. Přístup k portálu pro správu nástroje Visual Studio https://manage.visualstudio.com 

2. Vyhledejte předplatitele, který má neshodu hlavního názvu uživatele (UPN). (Funkce [Filter](search-license.md) může snadno najít předplatitele.)

3. Změňte přihlašovací e-mailovou adresu na hlavní název uživatele (UPN) odběratele. 

0. Uložit změny 

0. Informujte předplatitele, aby se odhlásil z portálu odběratele a znovu k němu přistoupí pomocí hlavního názvu uživatele. 

### <a name="personal-account-aliasing-issue"></a>Problém s aliasem osobního účtu

Pokud se e-mailová adresa použitá k přihlášení k portálu předplatných sady Visual Studio neshoduje s e-mailovou adresou přidruženou k předplatnému, může docházet k problémům i u osobních účtů. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Jak zjistit, jestli má váš účet osobní předplatné vliv na problém s aliasem

1. Přihlášení k https://my.visualstudio.com/subscriptions

0. Ověřte, že e-mailová adresa pro přihlášení uvedená v pravém horním rohu stránky odpovídá adrese, kterou jste použili k přihlášení.  Pokud se e-mailová adresa, která se přihlásila, neshoduje s e-mailovou adresou použitou pro přístup na web, dojde ke konfliktu mezi vaším účtem a aliasem.

#### <a name="how-to-fix-an-alias-issue"></a>Oprava problému s aliasem

Platforma sady Visual Studio určuje prioritu primárního aliasu, aby se zobrazily podrobnosti předplatného. 

1. Přejít ke **správě způsobu přihlášení k Microsoftu** Pokud se zobrazí výzva, přihlaste se ke svému účet Microsoft. 

2. V části Aliasy účtu vyberte **nastavit jako primární** vedle e-mailové adresy, která se používá k přiřazení předplatného. 

> [!div class="mx-imgBorder"]
> ![nastavit primární e-mailovou adresu](_img//aliasing/account-aliases.png)

3. Odhlaste se z portálu předplatných sady Visual Studio (https://my.visualstudio.com) 

4. Znovu se přihlaste pomocí účtu, který se používá k přiřazení předplatného, které se teď má nakonfigurovat jako primární alias. 

## <a name="preventing-aliasing-issues"></a>Prevence potíží s aliasy

Jako správce máte dvě možnosti, jak zajistit, aby vaši předplatitelé měli úspěšné přihlašování na [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- První možností (doporučeno) je použít účet adresáře jako přihlášení k portálu předplatných sady Visual Studio na https://my.visualstudio.com.  
- Druhá možnost (méně bezpečná) znamená, že se předplatitelům umožní přihlásit se pomocí jiné e-mailové adresy, než je jejich e-mailová adresa.

Obě tyto možnosti se konfigurují na portálu pro správu, a to provedením následujících kroků:  
1. Přihlaste se https://manage.visualstudio.com 

0. Pokud upravujete jednoho uživatele, vyberte tohoto uživatele v tabulce a klikněte pravým tlačítkem na Upravit. Otevře se panel, kde můžete upravit e-mailovou adresu přihlášení. V poli e-mailová adresa pro přihlášení proveďte potřebné aktualizace. Klikněte na Uložit a změny se projeví.  

0. Pokud potřebujete provést tyto změny velkému počtu uživatelů, můžete využít funkci hromadného úprav. Další informace najdete v článku věnovaném [úpravám více odběratelů pomocí hromadného úprav](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) .

> [!NOTE]
> U individuálních i hromadných změn předplatitel obdrží e-mail s pokyny, že se změnila e-mailová adresa pro přihlášení a bude se muset přihlásit pomocí aktualizované e-mailové adresy. Je také důležité si uvědomit, že pokud předplatitel předtím aktivoval výhody v rámci jiné přihlašovací adresy, bude muset pro přístup k nim nadále používat další přihlašovací adresu.  

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Určení maximálního využití](maximum-usage.md)


