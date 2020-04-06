---
title: 'Návod: Publikování rozšíření sady Visual Studio | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697141"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Návod: Publikování rozšíření Visual Studia

Tento návod ukazuje, jak publikovat rozšíření Sady Visual Studio na webu Visual Studio Marketplace. Když přidáte rozšíření na Marketplace, vývojáři mohou pomocí **rozšíření a aktualizací** vyhledat nová a aktualizovaná rozšíření.

## <a name="prerequisites"></a>Požadavky

 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Vytvoření rozšíření sady Visual Studio

Tento článek používá výchozí rozšíření VSPackage, ale kroky jsou platné pro všechny druhy rozšíření.

1. Vytvořte VSPackage v `TestPublish` C# s názvem, který má příkaz nabídky. Další informace naleznete v [tématu Vytvoření prvního rozšíření: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Zabalte rozšíření

1. Aktualizujte příponu *.vsixmanifest* se správnými informacemi o názvu produktu, autorovi a verzi.

   ![aktualizovat rozšíření vsixmanifest](media/update-extension-vsixmanifest.png)

2. Vytvořte rozšíření v režimu **vydání.** Nyní je rozšíření zabaleno jako VSIX ve složce \bin\Release.

3. Instalaci můžete ověřit poklepáním na vsix.

## <a name="test-the-extension"></a>Otestujte rozšíření

 Před distribucí rozšíření, sestavení a testování, abyste se ujistili, že je správně nainstalován v experimentální instanci sady Visual Studio.

1. V sadě Visual Studio spusťte ladění otevřít experimentální instanci sady Visual Studio.

2. V experimentální instanci přejděte do nabídky **Nástroje** a klepněte na **položku Rozšíření a aktualizace**. Rozšíření TestPublish by se mělo zobrazit v prostředním podokně a být povoleno.

3. V nabídce **Nástroje** zkontrolujte, zda se zobrazí příkaz test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publikování rozšíření na tržiště Sady Visual Studio

1. Ujistěte se, že jste vytvořili verzi rozšíření a že je aktuální.

2. Ve webovém prohlížeči otevřete web [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

3. V pravém horním rohu klikněte na **Přihlásit se**.

4. Přihlaste se pomocí svého účtu Microsoft. Pokud nemáte účet Microsoft, můžete jej v tomto okamžiku vytvořit.

5. Klepněte na **tlačítko Publikovat rozšíření**.  Tato možnost vás přenese na stránku pro správu pro všechna rozšíření. Pokud nemáte účet vydavatele, budete vyzváni k jeho vytvoření v tomto okamžiku.

   ![Nahrání na Marketplace](media/upload-to-marketplace.png)

6. Vyberte vydavatele, kterého chcete použít k nahrání rozšíření. Majitelé stránek můžete změnit kliknutím na jména vydavatelů uvedená vlevo. Klikněte na **Nové rozšíření** a vyberte **Visual Studio**.

7. V **1: Upload rozšíření**, můžete si vybrat nahrát soubor VSIX přímo na Visual Studio Marketplace nebo stačí přidat odkaz na vlastní webové stránky. V tomto příkladu rozšíření *TestPublish.vsix* je odeslána. Přetáhněte příponu nebo pomocí odkazu **pro kliknutí** vyhledejte soubor. Najděte rozšíření ve složce \bin\Release projektu.  Klikněte na **Pokračovat**.

8. V **2: Zadejte podrobnosti o rozšíření**, některá pole jsou automaticky vyplněna ze souboru *source.extension.vsixmanifest* z vaší přípony. Další podrobnosti o jednotlivých níže naleznete:

    * **Interní název se** používá v adrese URL stránky podrobností rozšíření. Například publikování rozšíření pod názvem vydavatele "myname" a zadání interní název jako "moje rozšíření" výsledky\.url "marketplace.visualstudio com/items?itemName=myname.myextension" pro stránku podrobností rozšíření.

    * **Zobrazovaný název** rozšíření. Tento název je automaticky vyplněn ze souboru *source.extension.vsixmanifest.*

    * **Číslo verze** rozšíření, které nahráváte. Tato verze je automaticky vyplněna ze souboru *source.extension.vsixmanifest.*

    * **ID VSIX** je jedinečný identifikátor, který visual studio používá pro vaše rozšíření. Tento identifikátor je povinný, pokud chcete, aby vaše rozšíření bylo automaticky aktualizováno. Tento identifikátor je automaticky vyplněn ze souboru *source.extension.vsixmanifest.*

    * **Logo,** které se používá pro vaše rozšíření. Toto logo je automaticky vyplněno ze souboru *source.extension.vsixmanifest,* pokud je k dispozici.

    * **Stručný popis** toho, co vaše rozšíření dělá. Tento popis je automaticky vyplněn ze souboru *source.extension.vsixmanifest.*

    * **Přehled** je dobrým místem pro zahrnutí snímků obrazovky a podrobných informací o tom, co vaše rozšíření dělá.

    * **Podporované verze sady Visual Studio** umožňují zvolit, na kterých verzích sady Visual Studio bude rozšíření fungovat. Rozšíření je nainstalováno pouze na tyto verze.

    * **Podporovaná edice Visual Studia umožňuje zvolit, na kterých edicích sady Visual Studio bude rozšíření fungovat. Rozšíření je nainstalováno pouze na tyto edice.

    * **Zadejte .** Nejběžnějším typem rozšíření jsou **nástroje**.

    * **Kategorie**. Vyzvedněte si až tři, které jsou nejvhodnější pro vaše rozšíření.

    * **Značky** jsou klíčová slova, která uživatelům pomáhají najít vaše rozšíření. Značky můžou zvýšit relevanci vyhledávání vašich rozšíření na Marketplace.

    * **Cenová kategorie** je cena vašeho rozšíření.

    * **Úložiště zdrojového kódu** umožňuje sdílet odkaz na zdrojový kód s komunitou.

    * **Povolit Q&A pro vaše rozšíření** umožňuje uživatelům opustit otázky na stránce položky rozšíření.

9. Klepněte na **tlačítko Uložit & nahrát**. Tato možnost vás přenese zpět na stránku správy vydavatele. Rozšíření ještě nebylo publikováno. Chcete-li rozšíření publikovat, klikněte na rozšíření pravým tlačítkem myši a vyberte **příkaz Zveřejnit**. Jak bude vaše rozšíření vypadat na Marketplace, můžete zobrazit tak, že vyberete **rozšíření zobrazení**. Chcete-li pořizovací čísla, klikněte na **položku Sestavy**. Chcete-li v rozšíření provést změny, klikněte na **tlačítko Upravit**.

   ![Nabídka položky rozšíření](media/extension-entry-menu.png)

10. Po kliknutí na **možnost Zveřejnit**je rozšíření nyní veřejné. Vyhledejte rozšíření na webu Visual Studio Marketplace.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Přidání dalších uživatelů ke správě účtu majitele stránek

Marketplace podporuje udělení oprávnění dalším uživatelům k přístupu a správě účtu vydavatele.

1. Přejděte na účet vydavatele, ke kterým chcete přidat další uživatele.

2. Vyberte **členové** a klikněte na **Přidat**.

   ![Přidat dalšího uživatele](media/add-users.png)

3. Potom můžete zadat e-mailovou adresu uživatele, který chcete přidat, a udělit správnou úroveň přístupu v části **Vybrat roli**.  Máte na výběr z následujících možností:

   * **Tvůrce**: Uživatel může publikovat rozšíření, ale nemůže zobrazit nebo spravovat rozšíření publikovaná jinými uživateli.

   * **Čtečka**: Uživatel může zobrazit rozšíření, ale nemůže publikovat ani spravovat rozšíření.

   * **Přispěvatel**: Uživatel může publikovat a spravovat rozšíření, ale nemůže upravovat nastavení vydavatele ani spravovat přístup.

   * **Vlastník**: Uživatel může publikovat a spravovat rozšíření, upravovat nastavení vydavatele a spravovat přístup.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instalace rozšíření z webu Visual Studio Marketplace

Teď, když je rozšíření publikováno, nainstalujte ho do sady Visual Studio a otestujte jej tam.

1. V sadě Visual Studio klikněte v nabídce **Nástroje** na **položku Rozšíření a aktualizace**.

2. Klepněte na **tlačítko Online** a vyhledejte **položku TestPublish**.

3. Klepněte na tlačítko **Stáhnout**. Rozšíření je pak naplánováno pro instalaci.

4. Chcete-li dokončit instalaci, zavřete všechny instance sady Visual Studio.

## <a name="remove-the-extension"></a>Odebrání rozšíření

Rozšíření můžete odebrat z webu Visual Studio Marketplace a z počítače.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Odebrání rozšíření z webu Visual Studio Marketplace

1. Otevřete web [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

2. V pravém horním rohu klikněte na **Publikovat** rozšíření. Vyberte vydavatele, který jste použili k publikování **Aplikace TestPublish**. Zobrazí se výpis pro **TestPublish.**

3. Klikněte pravým tlačítkem myši na položku rozšíření a klepněte na příkaz **Odebrat**. Budete vyzváni k potvrzení, zda chcete rozšíření odebrat. Klikněte na tlačítko **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Odebrání rozšíření z počítače

1. V sadě Visual Studio klikněte v nabídce **Nástroje** na **položku Rozšíření a aktualizace**.

2. Vyberte **TestPublish** a klepněte na tlačítko **Odinstalovat**. Rozšíření je pak naplánováno na odinstalaci.

3. Chcete-li provést odinstalaci, zavřete všechny instance sady Visual Studio.
