---
title: 'Návod: Publikování rozšíření sady Visual Studio | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae0b9d48e2a2292229b40e3aaf2a1c755e4c844e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815738"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Návod: Publikování rozšíření sady Visual Studio

Tento návod ukazuje, jak publikovat rozšíření sady Visual Studio pro Visual Studio Marketplace. Když přidáte rozšíření na webu Marketplace, vývojáři mohou použít **rozšíření a aktualizace** a vyhledejte nové a aktualizované rozšíření.

## <a name="prerequisites"></a>Požadavky

 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Vytvoření rozšíření sady Visual Studio

Tento článek používá výchozí rozšíření VSPackage, ale postup je platná pro všechny typy rozšíření.

1. Vytvoření v jazyce C# s názvem VSPackage `TestPublish` , která obsahuje příkaz nabídky. Další informace najdete v tématu [vytvořit své první rozšíření: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Balíček rozšíření

1. Aktualizovat rozšíření *.vsixmanifest* se správnými informacemi o názvu produktu, autora a verzi.

   ![aktualizace rozšíření vsixmanifest](media/update-extension-vsixmanifest.png)

2. Vytváření rozšíření **vydání** režimu. Rozšíření je teď součástí jako rozšíření VSIX ve složce \bin\Release.

3. Poklepejte na položku VSIX k ověření instalace.

## <a name="test-the-extension"></a>Testování rozšíření

 Před distribucí rozšíření, sestavit a otestovat a ujistit se, že je v experimentální instanci sady Visual Studio správně nainstalované.

1. V sadě Visual Studio spusťte ladění spustíte experimentální instanci sady Visual Studio.

2. V experimentální instanci aplikace, přejděte **nástroje** nabídky a klikněte na tlačítko **rozšíření a aktualizace**. Rozšíření TestPublish by se měla objevit v prostředním podokně a povolit.

3. Na **nástroje** nabídky, ujistěte se, že se zobrazí příkaz test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publikování rozšíření pro Visual Studio Marketplace

1. Ujistěte se, že jste vytvořili na prodejní verzi produktu rozšíření a zda je aktuální.

2. Ve webovém prohlížeči otevřete [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) webu.

3. V pravém horním rohu klikněte na tlačítko **přihlášení**.

4. K přihlášení pomocí účtu Microsoft. Pokud nemáte účet Microsoft, můžete jeden vytvořit v tomto okamžiku.

5. Klikněte na tlačítko **publikování rozšíření**.  Tato možnost slouží k přejde na stránku spravovat vaše rozšíření. Pokud nemáte vydavatelského účtu, zobrazí se výzva k jeho vytvoření v tuto chvíli.

   ![Nahrát na web Marketplace](media/upload-to-marketplace.png)

6. Vyberte vydavatele, který chcete použít k nahrání rozšíření. Vydavatelé můžete změnit po kliknutí na názvy vydavatelů, které jsou uvedené na levé straně. Klikněte na **nové rozšíření** a vyberte **sady Visual Studio**.

7. V **1: nahrát rozšíření**, můžete k nahrání souboru VSIX přímo do Visual Studio Marketplace nebo jednoduše přidejte odkaz na vlastní web. V tomto příkladu, rozšíření, *TestPublish.vsix* nahraje. Přetáhněte rozšíření nebo použít **klikněte na tlačítko** odkaz k vyhledání souboru. Najdete rozšíření ve složce \bin\Release projektu.  Klikněte na tlačítko **pokračovat**.

8. V **2: zadání podrobností o rozšíření**, některá pole se vyplní automaticky z *source.extension.vsixmanifest* souboru z rozšíření. Najdete další podrobnosti o každé níže:

    * **Interní název** se používá v adrese URL stránky podrobností rozšíření. Příklad, výsledkem publikování rozšíření v části název vydavatele "Jmeno" a zadejte interní název být "rozšíření" URL "marketplace.visualstudio\.com/items?itemName=myname.myextension" podrobnosti tohoto rozšíření stránka.
    
    * **Zobrazovaný název** vašeho rozšíření. Tento název se vyplní automaticky z *source.extension.vsixmanifest* souboru.
   
    * **Verze** počet rozšíření hodláte nahrát. Tato verze se vyplní automaticky z *source.extension.vsixmanifest* souboru.
    
    * **VSIX ID** je jedinečný identifikátor, který sada Visual Studio používá pro rozšíření. Tento identifikátor je vyžadována, pokud by měl mít rozšíření automaticky aktualizovat. Tento identifikátor se vyplní automaticky z *source.extension.vsixmanifest* souboru.
    
   * **Logo** , který se používá pro rozšíření. Toto logo se vyplní automaticky z *source.extension.vsixmanifest* souboru, pokud je k dispozici.
    
     * **Krátký popis** toho, co dělá rozšíření. Tento popis se vyplní automaticky z *source.extension.vsixmanifest* souboru.
    
     * **Přehled** je vhodné místo zahrnout snímky obrazovky a podrobné informace o co dělá rozšíření.
    
     * **Podporované verze sady Visual Studio** umožní vybrat, které verze sady Visual Studio rozšíření bude fungovat na. Rozšíření je nainstalované jenom do těchto verzí.
    
     * ** Podporované edice umožňuje zvolit, jaké edice sady Visual Studio bude vaše rozšíření fungovat v sadě Visual Studio. Rozšíření je nainstalované jenom na tyto edice.
    
     * **Typ**. Jsou nejběžnějším typem rozšíření **nástroje**.
    
     * **Kategorie**. Můžete si vyberte až tři, které jsou nejvhodnější pro vaše rozšíření.
    
     * **Značky** jsou klíčová slova, které pomáhají uživatelům najít rozšíření. Značky pomáhají zvýšit relevanci vyhledávání rozšíření na webu Marketplace.
    
     * **Cenové kategorie** jsou náklady na vaše rozšíření.
    
     * **Úložiště zdrojového kódu** vám umožní sdílet odkaz na váš zdrojový kód s komunitou.
    
     * **Povolit Q & A pro své rozšíření** umožňuje uživatelům ponechte dotazy na stránce rozšíření položky.

9. Klikněte na tlačítko **uložit a nahrajte**. Tato možnost má zpět do vašeho vydavatele spravovat stránky. Rozšíření ještě nebyla publikována. Publikování rozšíření, klikněte pravým tlačítkem na rozšíření a vyberte **zveřejnit**. Můžete zobrazit, jak se vaše rozšíření bude vypadat na webu Marketplace výběrem **rozšíření zobrazení**. Získání čísel, klikněte na **sestavy**. Pokud chcete provést změny rozšíření, klikněte na **upravit**.

   ![Rozšíření položky nabídky](media/extension-entry-menu.png)

10. Po kliknutí na tlačítko **zveřejnit**, vaše rozšíření je teď veřejné. Hledat na Visual Studio Marketplace pro rozšíření.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Přidat další uživatele ke správě svého vydavatelského účtu

Web Marketplace podporuje uděluje uživatelům oprávnění pro přístup a správa vydavatelského účtu.

1. Přejděte do vydavatelského účtu, který chcete přidat další uživatele.

2. Vyberte **členy** a klikněte na **přidat**.

   ![Přidat další uživatele](media/add-users.png)

3. Potom můžete zadat e-mailovou adresu uživatele, který chcete přidat a udělit správnou úroveň přístupu v rámci **vybrat roli**.  Můžete použít jednu z následujících možností:

   * **Tvůrce**: uživatel mohl publikování rozšíření, ale nelze zobrazit nebo spravovat rozšíření publikovaných jinými uživateli.
  
   * **Čtečka**: uživatel mohl zobrazit rozšíření, ale nelze publikovat nebo spravovat rozšíření.
  
   * **Přispěvatel**: uživatel mohl publikovat a spravovat rozšíření, ale nelze upravit nastavení vydavatele nebo spravovat přístup.
  
   * **Vlastník**: uživatel můžete publikovat a spravovat rozšíření, upravit nastavení vydavatele a spravovat přístup.
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Nainstalovat rozšíření z Visual Studio Marketplace

Teď, když se publikuje rozšíření, nainstalujte ho v sadě Visual Studio a ho vyzkoušeli.

1. V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.

2. Klikněte na tlačítko **Online** a vyhledejte **TestPublish**.

3. Klikněte na tlačítko **Stáhnout**. Rozšíření se pak naplánovaná instalace.

4. K dokončení instalace, ukončete všechny instance sady Visual Studio.

## <a name="remove-the-extension"></a>Odebrat rozšíření

Rozšíření můžete odebrat z webu Visual Studio Marketplace a z vašeho počítače.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Odebrat rozšíření z Visual Studio Marketplace

1. Otevřít [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) webu.

2. V pravém dolním rohu klikněte na tlačítko **publikovat** rozšíření. Vyberte vydavatele, který jste použili k publikování **TestPublish**. Výpis **TestPublish** se zobrazí.

3. Klikněte pravým tlačítkem na položku rozšíření a klikněte na tlačítko **odebrat**. Zobrazí se výzva k potvrzení, pokud chcete odebrat rozšíření. Klikněte na tlačítko **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Odebrat rozšíření z počítače

1. V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.

2. Vyberte **TestPublish** a potom klikněte na tlačítko **odinstalovat**. Rozšíření se pak naplánovaná odinstalace.

3. K dokončení odinstalace, zavřete všechny instance sady Visual Studio.
