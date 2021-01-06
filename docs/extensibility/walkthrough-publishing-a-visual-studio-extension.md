---
title: 'Návod: publikování rozšíření sady Visual Studio | Microsoft Docs'
description: Naučte se publikovat rozšíření sady Visual Studio pro Visual Studio Marketplace, které vývojářům umožňuje vyhledat nová a aktualizovaná rozšíření.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbdd283c5d147c53e7d82843207b48d0dbf6e6e9
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877881"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Návod: publikování rozšíření sady Visual Studio

V tomto návodu se dozvíte, jak publikovat rozšíření sady Visual Studio na Visual Studio Marketplace. Když přidáte rozšíření na web Marketplace, můžou vývojáři použít **rozšíření a aktualizace** k vyhledání nových a aktualizovaných rozšíření.

## <a name="prerequisites"></a>Předpoklady

 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Vytvoření rozšíření pro Visual Studio

Tento článek používá výchozí rozšíření VSPackage, ale postup je platný pro všechny typy rozšíření.

1. Vytvořte VSPackage v jazyce C# s názvem `TestPublish` , který má příkaz nabídky. Další informace najdete v tématu [Vytvoření prvního rozšíření: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Zabalení rozšíření

1. Aktualizujte příponu *. vsixmanifest* správnými informacemi o názvu produktu, autorovi a verzi.

   ![aktualizovat rozšíření vsixmanifest](media/update-extension-vsixmanifest.png)

2. Sestavte rozšíření v režimu **vydání** . Rozšíření je teď zabalené jako VSIX ve složce \bin\Release.

3. Pokud chcete ověřit instalaci, můžete dvakrát kliknout na VSIX.

## <a name="test-the-extension"></a>Test rozšíření

 Před distribucí rozšíření ho Sestavte a otestujte, abyste se ujistili, že je správně nainstalovaný v experimentální instanci aplikace Visual Studio.

1. V aplikaci Visual Studio spusťte ladění a otevřete experimentální instanci sady Visual Studio.

2. V experimentální instanci přejděte do nabídky **nástroje** a klikněte na **rozšíření a aktualizace**. Rozšíření TestPublish by se mělo zobrazit v prostředním podokně a povolit.

3. V nabídce **nástroje** se ujistěte, že se zobrazí příkaz test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publikování rozšíření na Visual Studio Marketplace

1. Ujistěte se, že máte vytvořenou verzi pro vydání rozšíření a že je aktuální.

2. Ve webovém prohlížeči otevřete [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Web.

3. V pravém horním rohu klikněte na **Přihlásit** se.

4. Přihlaste se pomocí svého účet Microsoft. Pokud nemáte účet Microsoft, můžete si ho v tomto okamžiku vytvořit.

5. Klikněte na tlačítko **publikovat rozšíření**.  Tato možnost přejde na stránku Správa pro všechna vaše rozšíření. Pokud nemáte účet vydavatele, budete vyzváni k jeho vytvoření v tuto chvíli.

   ![Nahrát na Marketplace](media/upload-to-marketplace.png)

6. Vyberte vydavatele, který chcete použít k nahrání rozšíření. Vydavatele můžete změnit kliknutím na názvy vydavatelů, které jsou uvedeny na levé straně. Klikněte na **nové rozšíření** a vyberte **Visual Studio**.

7. V **1: nahrání rozšíření** se můžete rozhodnout odeslat soubor VSIX přímo do Visual Studio Marketplace nebo stačí přidat odkaz na svůj vlastní web. V tomto příkladu je Nahráno rozšíření *TestPublish. vsix* . Přetáhněte rozšíření nebo **použijte odkaz pro** vyhledání souboru. Najděte své rozšíření ve složce \bin\Release projektu.  Klikněte na **Pokračovat**.

8. Ve **2: zadejte podrobnosti o rozšíření**, některá pole se automaticky vyplní ze souboru *source. extension. vsixmanifest* z vašeho rozšíření. Další podrobnosti najdete tady:

    * **Interní název** se používá v adrese URL stránky s podrobnostmi rozšíření. Například publikováním rozšíření pod názvem vydavatele "jmena" a zadáním interního názvu, který má být "Moje rozšíření", má za následek adresu URL webu Marketplace. VisualStudio \. com/Items? název položky = jméno. MyExtension "pro stránku podrobností rozšíření.

    * **Zobrazovaný název** rozšíření Tento název se automaticky vyplní ze souboru *source. extension. vsixmanifest* .

    * Číslo **verze** rozšíření, které nahráváte. Tato verze je automaticky vyplněna ze souboru *source. extension. vsixmanifest* .

    * **VSIX ID** je jedinečný identifikátor, který Visual Studio používá pro vaše rozšíření. Tento identifikátor je vyžadován, pokud chcete, aby vaše rozšíření bylo automaticky aktualizováno. Tento identifikátor se automaticky vyplní ze souboru *source. extension. vsixmanifest* .

    * **Logo** , které se používá pro vaše rozšíření. Toto logo se automaticky vyplní ze souboru *source. extension. vsixmanifest* , pokud je k dispozici.

    * **Krátký popis** toho, co vaše rozšíření dělá. Tento popis se automaticky vyplní ze souboru *source. extension. vsixmanifest* .

    * **Přehled** je dobrým místem, kde můžete zahrnout snímky obrazovky a podrobné informace o tom, co vaše rozšíření dělá.

    * **Podporované verze sady Visual Studio** vám umožní zvolit, na kterých verzích sady Visual Studio bude rozšíření fungovat. Vaše rozšíření je nainstalováno pouze do těchto verzí.

    * * * Podporovaná edice sady Visual Studio vám umožní zvolit, na kterých edicích aplikace Visual Studio bude rozšíření fungovat. Vaše rozšíření je nainstalované jenom v těchto edicích.

    * **Zadejte**. Nejběžnějším typem rozšíření jsou **nástroje**.

    * **Kategorie**. Vyberte maximálně tři, které jsou vhodné pro vaše rozšíření.

    * **Značky** jsou klíčová slova, která uživatelům pomůžou najít vaše rozšíření. Značky mohou zvýšit relevanci hledání vašich rozšíření na webu Marketplace.

    * **Cenová kategorie** je cena za vaše rozšíření.

    * **Úložiště zdrojového kódu** umožňuje sdílet odkaz na zdrojový kód s komunitou.

    * Možnost **Q&A pro vaše rozšíření** umožňuje uživatelům zanechat otázky na stránce s položkou rozšíření.

9. Klikněte na **uložit & nahrát**. Tato možnost vrátí zpět na stránku pro správu vašeho vydavatele. Vaše rozšíření ještě není publikované. Pokud chcete své rozšíření publikovat, klikněte pravým tlačítkem na rozšíření a vyberte **nastavit jako veřejné**. Výběrem možnosti **Zobrazit rozšíření** můžete zobrazit, jak bude rozšíření vypadat na webu Marketplace. V případě čísel získání klikněte na **sestavy**. Chcete-li změnit rozšíření, klikněte na tlačítko **Upravit**.

   ![Nabídka položky rozšíření](media/extension-entry-menu.png)

10. Po kliknutí **na zveřejnit je** rozšíření teď veřejné. Vyhledejte Visual Studio Marketplace pro vaše rozšíření.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Přidat další uživatele pro správu účtu vydavatele

Marketplace podporuje udělení dalších oprávnění uživatelům k přístupu a správě účtu vydavatele.

1. Přejděte na účet vydavatele, do kterého chcete přidat další uživatele.

2. Vyberte **členy** a klikněte na **Přidat**.

   ![Přidat dalšího uživatele](media/add-users.png)

3. Pak můžete zadat e-mailovou adresu uživatele, kterého chcete přidat, a udělit správnou úroveň přístupu v rámci **Vybrat roli**.  Máte na výběr z následujících možností:

   * **Creator**: uživatel může publikovat rozšíření, ale nemůže zobrazit ani spravovat rozšíření publikovaná jinými uživateli.

   * **Čtecí modul**: uživatel může zobrazit rozšíření, ale nemůže publikovat nebo spravovat rozšíření.

   * **Přispěvatel**: uživatel může publikovat a spravovat rozšíření, ale nemůže upravovat nastavení vydavatele ani spravovat přístup.

   * **Vlastník**: uživatel může publikovat a spravovat rozšíření, upravovat nastavení vydavatele a spravovat přístup.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Nainstalovat rozšíření z Visual Studio Marketplace

Teď, když je rozšíření publikované, nainstalujte ho v aplikaci Visual Studio a otestujte tam.

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace**.

2. Klikněte na **online** a vyhledejte **TestPublish**.

3. Klikněte na **Stáhnout**. Rozšíření je pak naplánováno pro instalaci.

4. Chcete-li dokončit instalaci, zavřete všechny instance aplikace Visual Studio.

## <a name="remove-the-extension"></a>Odebrání rozšíření

Rozšíření můžete odebrat z Visual Studio Marketplace a z počítače.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Odebrání rozšíření z Visual Studio Marketplace

1. Otevřete web [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) .

2. V pravém horním rohu klikněte na **publikovat** rozšíření. Vyberte vydavatele, kterého jste použili k publikování **TestPublish**. Zobrazí se výpis pro **TestPublish** .

3. Klikněte pravým tlačítkem myši na položku rozšíření a klikněte na tlačítko **Odebrat**. Zobrazí se výzva k potvrzení, zda chcete rozšíření odebrat. Klikněte na **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Odebrání rozšíření z počítače

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace**.

2. Vyberte **TestPublish** a pak klikněte na **odinstalovat**. Rozšíření je pak naplánováno pro odinstalaci.

3. Chcete-li dokončit odinstalaci, zavřete všechny instance aplikace Visual Studio.
