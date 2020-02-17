---
title: Přihlášení k předplatným sady Visual Studio může při použití aliasů selhat. | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: Přihlášení se nemusí zdařit, pokud se používají aliasy nebo popisné názvy.
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276617"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Přihlášení k předplatným sady Visual Studio může při použití aliasů selhat.
V závislosti na typu účtu použitého k přihlášení se nemusí při přihlašování k [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)správně zobrazit dostupná předplatná. Jednou z možných příčin je použití "aliasů" nebo "popisných názvů" místo přihlašovací identity, ke které je předplatné přiřazeno. Tento název se nazývá "aliasing".

## <a name="what-is-aliasing"></a>Co je aliasing?
Pojem "aliasing" odkazuje na uživatele, kteří mají různé identity pro přihlášení k Windows (nebo službě Active Directory) a pro přístup k e-mailu.

Aliasing se dá využít, když má společnost Microsoft Online Service pro své adresáře, jako je napříkladolivia@contoso.com, ale uživatelé mají přístup k e-mailovým účtům pomocí aliasů nebo popisných názvů, jako je například "OliviaG@contoso.com". Zajistěte, aby se uživatelé přihlásili pomocí e-mailové adresy pro přihlášení, jak je uvedeno na portálu pro správu předplatných sady Visual Studio na https://manage.visualstudio.com pro přístup ke svým předplatným.

## <a name="as-an-administrator-what-options-do-i-have"></a>Jaké možnosti mám k dispozici jako správce?

V závislosti na typu účtu předplatitele Najděte příslušné řešení níže:

### <a name="work-or-school-account-upn-mismatch-issue"></a>Problém s neshodou uživatelského jména v pracovním nebo školním účtu

Neshoda hlavního názvu uživatele (UPN) se může vyskytnout, když má compnay aktivní Diretory, kde hlavní název uživatele není stejný jako primární adresa SMTP. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>Jak zjistit, jestli má přihlašovací adresa uživatele neshodu hlavního názvu uživatele

Dokončete uživatele podle následujících kroků:

1. Přihlaste se k https://my.visualstudio.com pomocí přihlašovací adresy uvedené v e-mailu s přiřazením předplatného.  

    > [!NOTE]
    > Pokud nemají e-maily s přiřazením předplatného, můžete je znovu odeslat z portálu pro správu.  

2. Klikněte na kartu **předplatná** .
3. Ověřte, že se e-mailová adresa zobrazuje v pravém horním rohu, kde se zobrazí zpráva "jste přihlášení jako...". je stejná jako e-mailová adresa přihlášení v e-mailu přiřazení předplatného.  Pokud ne, nebudou mít přístup k výhodám jejich předplatného. 

   > [!div class="mx-imgBorder"]
   > Stránka předplatná ![](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>Oprava neshody hlavního názvu uživatele (UPN)

1. Přístup k portálu pro správu sady Visual Studio na https://manage.visualstudio.com 

2. Vyhledejte uživatele, který má neshodu hlavního názvu uživatele (UPN).  Funkce [Filter](search-license.md) může tuto funkci usnadnit, pokud máte spoustu předplatných. 

3. Změňte přihlašovací e-mailovou adresu na hlavní název uživatele (UPN).

4. Uložit změny 

5. Požádejte uživatele, aby si odhlásil portál odběratele a znovu se přihlásil pomocí hlavního názvu uživatele (UPN).   

### <a name="personal-account-aliasing-issue"></a>Problém s aliasem osobního účtu

Problémy s aliasy můžou mít dopad i na osobní účty. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>Jak zjistit, jestli má osobní účet problém s aliasem

1. Přihlaste se https://my.visualstudio.com.

2. Klikněte na kartu **předplatná** a ověřte adresu, ke které jste se přihlásili. 

3. Pokud se e-mailová adresa, která se přihlásila, neshoduje s e-mailovou adresou použitou pro přístup na web, dojde ke konfliktu mezi vaším účtem a aliasem. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>Oprava potíží s aliasem osobního účtu

Platforma předplatných sady Visual Studio nastaví prioritu primárního aliasu pro zobrazení podrobností o předplatném.  Chcete-li tento problém vyřešit, je třeba vytvořit jiný alias e-mailu, který váš primární alias pro přihlášení. 

1. Přejít ke [správě způsobu přihlášení k Microsoftu](https://go.microsoft.com/fwlink/p/?linkid=842796)
2. Pokud se zobrazí výzva, přihlaste se ke svému účet Microsoft. 
3. V části Aliasy účtu vyberte **nastavit jako primární** vedle e-mailové adresy, která se používá k přiřazení předplatného. 
4. V části Aliasy účtu vyberte nastavit jako primární vedle e-mailové adresy, která se používá k přiřazení předplatného. 
5. Odhlaste se z portálu pro předplatitele sady Visual Studio (https://my.visualstudio.com) 
6. Znovu přistoupit k portálu pomocí nového primárního aliasu. 

### <a name="ensure-a-successful-experience-for-your-users"></a>Zajištění úspěšného prostředí pro uživatele

Jako správce máte dvě možnosti, jak zajistit, aby vaši předplatitelé měli úspěšné přihlašování na https://my.visualstudio.com. 

- První možnost (doporučeno) je využití účtu adresáře jako přihlašovací adresy v https://manage.visualstudio.com.
- Druhá možnost, která je méně bezpečná, druhá možnost (méně bezpečná) znamená, že se předplatitelům umožní přihlásit pomocí jiné e-mailové adresy, než je jejich e-mailová adresa adresáře.

Obě možnosti se konfigurují na portálu pro správu, a to provedením následujících kroků:

1. Přihlaste se https://manage.visualstudio.com 

2. Pokud upravujete jednoho uživatele, vyberte tohoto uživatele v tabulce a klikněte pravým tlačítkem na Upravit. Otevře se panel, kde můžete upravit e-mailovou adresu přihlášení.  

3. V poli e-mailová adresa pro přihlášení proveďte potřebné aktualizace. 

4. Klikněte na Uložit a změny se projeví.  
Pokud potřebujete provést tyto změny velkému počtu uživatelů, můžete využít funkci hromadného úprav. Další informace o tomto procesu najdete v části **Úprava více předplatitelů pomocí hromadného úprav** v článku [Edit Subscriptions]] (edit-License.MD).  

## <a name="next-steps"></a>Další kroky
Přečtěte si další informace o správě předplatných sady Visual Studio.
- [Přiřazení jednotlivých předplatných](assign-license.md)
- [Přiřazení více předplatných](assign-license-bulk.md)
- [Úprava předplatných](edit-license.md)
- [Odstranění předplatných](delete-license.md)
- [Určení maximálního využití](maximum-usage.md)

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](/visualstudio/)
- [Dokumentace ke službě Azure DevOps](/azure/devops/)
- [Dokumentace k Azure](/azure/)
- [Dokumentace k Microsoft 365](/microsoft-365/)
