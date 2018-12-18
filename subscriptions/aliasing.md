---
title: Přihlášení k předplatná sady Visual Studio může selhat při použití aliasy | Dokumentace Microsoftu
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/02/2018
ms.topic: Get-Started-Article
description: Přihlášení může selhat, pokud se používají aliasy nebo popisné názvy
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 3743cc11d5001d12ba4cd030ddc0cfc914db3131
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817435"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Přihlášení k předplatná sady Visual Studio může selhat, pokud aliasy using

V závislosti na typu účtu, použili pro přihlášení, nemusí být správně zobrazovat dostupná předplatná při přihlašování k [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Jednou z možných příčin je použití "aliasy" nebo "popisné názvy" místo identity přihlášení ke kterému je přiřazené předplatné. Tomu se říká "aliasy".

## <a name="what-is-aliasing"></a>Co je aliasing?

Pojem "aliasy" představuje uživatelé mají různé identity pro přihlášení k Windows (nebo službě Active Directory) a pro přístup k e-mailu.

Aliasy může dojít, když má společnost Microsoft Online Service pro adresář přihlášení, jako je třeba JohnD@contoso.com, ale uživatelé přístup k jejich e-mailové účty pomocí aliasů nebo popisné názvy, například John.Doe@contoso.com. Pro mnoho zákazníků, kteří spravují svá předplatná prostřednictvím na svazek licencování Service Center (VLSC), může dojít k úspěšné prostředí přihlásit jako e-mailovou adresu za předpokladu (John.Doe@contoso.com) neodpovídá adrese adresáře (JohnD@contoso.com) požadované pro úspěšné ověření prostřednictvím možnosti "Pracovní nebo školní účet".

## <a name="as-an-administrator-what-options-do-i-have"></a>Jako správce jaké jsou možnosti?

Jako správce, existují dvě možnosti, vaši předplatitelé měli prostředí úspěšné přihlášení [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs).
- První možnost (doporučeno), je využít adresář účtu jako přiřazenou adresu v Volume Licensing Service Center (VLSC). Odkazovat na [přiřazení předplatitele adresář účtu](#assigning-subscribers-to-a-directory-account) části v tomto článku najdete další podrobnosti.
- (Méně bezpečné), druhou možností je povolit vaši předplatitelé (označovaný také jako přidružení e-mailová adresa "Pracovní nebo školní" na "Osobní" účet Účet Microsoft nebo MSA). Odkazovat na [definování pracovního nebo školního účtu jako osobní účet ](#defining-a-work-or-school-account-as-a-personal-account ) části v tomto článku najdete další podrobnosti.

> [!NOTE]
> Jakmile se vaše společnost je migrovat na nová předplatná sady Visual Studio [portálu pro správu](https://manage.visualstudio.com), budete moci využít výhod tohoto nového prostředí správy, což umožní adresáře a e-mailové adresy poskytované v rámci profil účastníka. Další informace o [migrace](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Jako předplatitel jaké jsou možnosti?

Z hlediska předplatitele je důležité pro první práci se svým správcem o konfigurace identity vaší společnosti. V případě potřeby správce pravděpodobně nutné aktualizovat nastavení vašeho účtu ze svého portálu pro správu nebo budete muset vytvořit účet Microsoft (MSA) pomocí podnikové e-mailovou adresu. Před přepnutím kroky k vytvoření MSA, mluví se svým správcem o všech zásad nebo problémy s provedením této akce. Odkazovat na [definování pracovního nebo školního účtu jako osobní účet](#defining-a-work-or-school-account-as-a-personal-account) části v tomto článku najdete další podrobnosti.

## <a name="assigning-subscribers-to-a-directory-account"></a>Přiřadit předplatitele adresář účtu

Ve všech případech se správce předplatného v rámci Volume Licensing Service Center (VLSC) musíte použít adresu adresáře pro nové předplatitele nebo předplatitelům "existující" aktualizaci e-mailovou adresu. Je důležité si uvědomit, že pomocí adresa adresáře bude znamenat žádné nové předplatitele neobdrží Uvítacího e-mailu a správce muset informovat odběratele, které jim byly přiřazeny předplatné. Po následujícím níže uvedené kroky, také můžete použít e-mailu [šablony](#notifying-your-subscribers-with-directory-addresses) oznámit vaši předplatitelé a pomoci prostřednictvím procesu přihlášení.

### <a name="adding-new-subscribers"></a>Přidání nové předplatitele

Postupujte podle těchto kroků pro přidání nového odběratele s účtem služby adresáře.

1. Přejděte [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) a přihlaste se.
2. Na stránce Správce VLSC klikněte na tlačítko **předplatná** a potom **předplatných sady Visual Studio**.

    > [!div class="mx-imgBorder"]
    > ![Nabídka předplatného](_img//vlsc/vlsc-subscriptions.png)


3. Klikněte na tlačítko **číslo smlouvy** přidružený k předplatnému sady Visual Studio.

    > [!div class="mx-imgBorder"]
    > ![Vyberte smlouvy](_img/vlsc/vlsc-agreement.png)

4. Klikněte na tlačítko **přiřazení předplatného**.
5. Vyberte požadovaný **úroveň předplatného**.
6. Ověření máte předplatné k dispozici chcete přiřadit a klikněte na tlačítko **Další**.
7. Zadejte podrobné údaje o předplatitelích a adresu adresáře do pole e-mailovou adresu a klikněte na tlačítko **Další**.
8. Ověřte informace o odběrateli a klikněte na **Dokončit**.
9. Oznámení odběrateli, že svoje předplatné se zřizují pomocí níže [šablony](#notifying-your-subscribers-with-directory-addresses).

### <a name="updating-an-existing-subscriber"></a>Aktualizace stávající předplatitel

Postupujte prosím podle následujících kroků aktualizujte stávající předplatitel s účtem služby adresáře.

1. Přejděte [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) a přihlaste se.
2. Na stránkách správce VLSC klikněte na **předplatná** a potom **předplatných sady Visual Studio**.
3. Klikněte na tlačítko **číslo smlouvy** přidružený k předplatnému sady Visual Studio.
4. Klikněte na tlačítko **šipka dolů** na vyhledávacím panelu.
5. Vyhledejte předplatitele. pomocí pole "E-mailová adresa".
6. V seznamu výsledků klepněte **příjmení** odběratele.
7. Klikněte na tlačítko **upravit**.
8. Změňte pole e-mailovou adresu na adresu požadovaném adresáři a klikněte na tlačítko **Uložit**.
9. Oznámení odběrateli, že svoje předplatné se zřizují pomocí následující e-mailové šablony.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Upozornění vašim předplatitelům s adresami adresáře

Protože Uvítacího e-mailu úspěšně nedostanou vaše odběratele, zkopírujte a vložte níže zpráv do e-mailu a odeslat do vašich odběratele. Nahraďte odpovídajícími informacemi pro každý předplatitel % slova.

---Kopírování níže (Ctrl + C)---

Hello % odběratele názvem %

Máte přiřazené předplatné sady Visual Studio. Navštivte prosím https://my.visualstudio.coma přihlaste se pomocí % % adresu adresáře a aktivovat přístup k vašemu předplatnému.

Pokud máte potíže, kontaktujte prosím tým podpory (https://visualstudio.microsoft.com/subscriptions/support/).

V dolní části stránky vyberte následující položky:
   - Účtů, předplatných a podpora pro fakturaci
   - Od vydání zvolit přihlašovací předplatné podpory
   - Zvolte odpovídající zemi
   - Vyberte požadovanou možnost podpory s asistencí

---Konec zkopírování---

## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Definování pracovního nebo školního účtu jako osobní účet

Prosím využít pokynů v tématu [přiřazení předplatitele adresář účtu](#assigning-subscribers-to-a-directory-account) části k přidání nového uživatele nebo aktualizaci e-mailovou adresu uživatele v rámci Volume Licensing Service Center (VLSC).  V případech, kde není rozpoznána e-mailovou adresu adresáře bude uživatel muset projít procesem vytvoření nového účtu k definování e-mailovou adresu jako osobní účet.  Pro krátkodobou tým předplatných sady Visual Studio má zabezpečené výjimku z níže definovanou zásadu identity, ale můžeme společností investuje do funkce potřeba odebrat tyto zásady.

> [!WARNING]
> Microsoft nedoporučuje kombinace identity "Pracovní nebo školní" s "Osobní" identit.  Tato akce způsobí, že organizace ke ztrátě vlastnictví a kontrolu nad účet a zaměstnanci měli dál přístup k určité produkty nebo služby, dokonce i potom, co odejdete společnosti.  Najdete v tomto [blogový příspěvek](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/), od týmu Microsoft Identity, další informace.

### <a name="defining-an-email-address-as-a-personal-account"></a>Definování e-mailovou adresu jako osobní účet

Po přiřazení předplatného je k odběrateli, dostanou e-mail s požadavkem na web [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) výhod svých předplatitelských výhod.  Při pokusu o přihlášení, přihlášení předplatné sady Visual Studio dojde k selhání s chyba oznamující, že účet nebyl rozpoznán.  Před přihlášením na stránce [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) prostředí, požádejte vašeho odběratele postupujte podle následujících pokynů.  Pokud nezbytné, může být využit [šablony](#notifying-your-subscribers-using-personal-accounts) oznámit vaše odběratele po přiřazení předplatného.

1. Přejděte do https://my.visualstudio.coma klikněte na tlačítko **vytvořit nový účet Microsoft**.

2. Vyplňte pole:
   - Zadejte e-mailovou adresu, který obdržel Uvítacího e-mailu v Someone@example.com pole
   - Vytvořit heslo
   - Zvolte nastavení propagační akce
   - Klikněte na tlačítko **další**

3. Proveďte kroky ověření a klikněte na tlačítko **Další**.

4. Noví uživatelé muset vyplnit profil pro Visual Studio.

5. Předplatné a výhody by měla nyní být viditelné.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Upozornění vašim předplatitelům s využitím osobní účty

Ve scénáři uvedeném výše vaši předplatitelé dostanou "Uvítací E-mail", ale kvůli aliasy, které se můžou vyskytnout, že se že nebudou moct přihlásit.  Můžete použít následující text, který má upozornit vaši předplatitelé výše uvedené kroky a doporučuje možnosti podpory v případě potřeby.  Nahraďte odpovídajícími informacemi pro každý předplatitel % slova.

---Kopírování níže (Ctrl + C)---

Hello % odběratele názvem %

Bylo přiřazeno předplatné sady Visual Studio a mohou směrováni pro přihlášení k https://my.visualstudio.com podle Uvítacího e-mailu.  Když je správný webu pro využívání výhod, naše organizace vyžaduje, abyste provést několik kroků navíc pro přístup k webu.  Postupujte prosím podle následujících pokynů, které vám pomohou vytvořit "Account Microsoft", který se váže na našich firemních e-mailovou adresu.  Po dokončení těchto kroků se použije pro přístup k výhodám předplatného e-mailovou adresu.
1. Navštivte web https://my.visualstudio.com

2. Klikněte na tlačítko Vytvořit nový Account Microsoft na pravé straně

3. Vyplňte formulář:
   - Použijte váš firemní e-mailovou adresu v someone@example.com pole
   - Zadejte heslo
   - Vyberte preferovaný propagační akce
   - Klikněte na tlačítko Další

4. Dokončete ověření účtu

5. V případě potřeby vyplnit profil pro Visual Studio

6. Teď byste měli vidět vaše výhody

Poznámka: Při návštěvě https://my.visualstudio.com v budoucnu, můžete být vyzváni k výběru účtu, který chcete použít (např.) "Pracovní nebo školní účet" nebo "Osobní účet").  Po provedení výše uvedených kroků, bude muset využít možnost osobní účet.".

Pokud máte potíže, kontaktujte prosím tým podpory (https://visualstudio.microsoft.com/subscriptions/support/).

V dolní části stránky vyberte následující položky:
   - Účtů, předplatných a podpora pro fakturaci
   - Od vydání zvolit přihlašovací předplatné podpory
   - Zvolte odpovídající zemi
   - Vyberte požadovanou možnost podpory s asistencí

---Konec zkopírování---
