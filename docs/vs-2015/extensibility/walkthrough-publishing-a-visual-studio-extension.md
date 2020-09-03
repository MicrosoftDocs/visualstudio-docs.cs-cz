---
title: Publikování rozšíření | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201970"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Návod: Publikování rozšíření sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Poznámka**: galerie sady Visual Studio se nahrazuje Visual Studio Marketplace. Podrobnosti najdete v nejnovější verzi tohoto tématu.

V tomto návodu se dozvíte, jak publikovat rozšíření sady Visual Studio v galerii sady Visual Studio. Když přidáte rozšíření do galerie, můžou vývojáři použít **rozšíření a aktualizace** k vyhledání nových a aktualizovaných rozšíření.

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Vytvoření rozšíření pro Visual Studio
 V tomto případě použijeme výchozí rozšíření VSPackage, ale stejný postup je platný pro všechny typy rozšíření.

1. Vytvořte VSPackage v jazyce C# s názvem `TestPublishing` , který má příkaz nabídky. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Test rozšíření
 Před distribucí rozšíření si ho Sestavte a otestujte, abyste se ujistili, že je správně nainstalovaný v experimentální instanci aplikace Visual Studio.

1. V aplikaci Visual Studio spusťte ladění. pro otevření experimentální instance sady Visual Studio.

2. V experimentální instanci přejděte do nabídky **nástroje** a klikněte na **Správce rozšíření**. Rozšíření TestPublishing by se mělo zobrazit v prostředním podokně a povolit.

3. V nabídce **nástroje** se ujistěte, že se zobrazí příkaz test.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publikování rozšíření v galerii sady Visual Studio
 Nyní můžete rozšíření publikovat do galerie sady Visual Studio.

1. Ujistěte se, že máte vytvořenou verzi pro vydání rozšíření a že je aktuální.

2. Ve webovém prohlížeči otevřete [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Web.

3. V pravém horním rohu klikněte na **Přihlásit**se.

4. Přihlaste se pomocí svého účet Microsoft. Pokud nemáte účet Microsoft, můžete si ho v tomto okamžiku vytvořit.

5. Klikněte na **Odeslat**.

6. V **kroku 1: typ rozšíření**, vyberte **Nástroj** a pak klikněte na **Další**.

7. V **kroku 2: nahrání**můžete odeslat přímo do galerie sady Visual Studio nebo jenom přidat odkaz na svůj vlastní web. V tomto případě vyberte možnost **Chci nahrát nástroj**. Zobrazí se okno **výběr ovládacího prvku** . Klikněte na **Procházet** a pak ve složce \bin\Release projektu vyberte TestPublish. VSIX. Klikněte na **Next** (Další).

8. V **kroku 3: zobrazí se základní informace o**polích ze souboru source. extension. vsixmanifest. Vyberte příslušnou **kategorii** a přidejte **značky** , které uživatelům pomůžou najít vaše rozšíření. Možná budete chtít přidat podrobnější souhrn a popis (popis musí mít minimálně 280 znaků, dlouhý). Ponechte **typ rozšíření** jako **rozšíření společnosti Microsoft** a **nákladovou kategorii** jako **zkušební verzi**.

9. Přečtěte si smlouvu o příspěvcích na konci stránky a vraťte se **Souhlasím**.

10. Klikněte na **vytvořit příspěvek**. Tím se zobrazí stránka, kterou rozšíření bude mít v galerii sady Visual Studio, a zobrazí se zpráva, že stránka ještě nebyla publikována.

11. Klikněte na **Publikovat**.

12. Vyhledejte v galerii sady Visual Studio své rozšíření. Zobrazí se výpis rozšíření TestPublish.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Instalace rozšíření z galerie sady Visual Studio
 Teď, když je rozšíření publikované, nainstalujte ho v aplikaci Visual Studio a otestujte tam.

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace**.

2. Klikněte na **online** a vyhledejte TestPublish. Zobrazí se výpis rozšíření TestPublish.

3. Klikněte na tlačítko **Stáhnout**. Po stažení rozšíření klikněte na **nainstalovat**.

4. Chcete-li dokončit instalaci, restartujte aplikaci Visual Studio.

## <a name="removing-the-extension"></a>Odebrání rozšíření
 Rozšíření můžete odebrat z galerie sady Visual Studio a z počítače.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Odebrání rozšíření z galerie sady Visual Studio

1. Otevřete web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

2. V pravém horním rohu klikněte na **Moje Extenions**. Zobrazí se výpis pro TestPublish.

3. Klikněte na tlačítko **Odstranit**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Odebrání rozšíření z počítače

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na **Správce rozšíření**.

2. Vyberte TestPublish a pak klikněte na **odinstalovat**.

3. Chcete-li dokončit odinstalaci, restartujte aplikaci Visual Studio.
