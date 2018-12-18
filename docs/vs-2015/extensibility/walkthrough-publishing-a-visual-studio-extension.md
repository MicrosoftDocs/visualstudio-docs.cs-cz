---
title: Publikování rozšíření | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e67c0c6b1bf24555e57d09b75317ce562a9f956
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063024"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Návod: Publikování rozšíření sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Poznámka:**: The Galerie sady Visual Studio teď nahrazuje Visual Studio Marketplace. Zobrazte nejnovější verzi tohoto tématu podrobnosti.


Tento návod ukazuje, jak publikovat rozšíření sady Visual Studio do Galerie Visual Studio. Po přidání rozšíření v galerii se mohou vývojáři **rozšíření a aktualizace** a vyhledejte nové a aktualizované rozšíření existuje.

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Vytvoření rozšíření sady Visual Studio
 V tomto případě použijeme rozšíření VSPackage výchozí, ale stejný postup platí pro každý typ rozšíření.

1.  Vytvoření v jazyce C# s názvem VSPackage `TestPublishing` , která obsahuje příkaz nabídky. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Testování rozšíření
 Před distribucí rozšíření, sestavit a otestovat a ujistit se, že je v experimentální instanci sady Visual Studio správně nainstalované.

1.  V sadě Visual Studio spusťte ladění. Chcete-li spustit experimentální instanci sady Visual Studio.

2.  V experimentální instanci aplikace, přejděte **nástroje** nabídky a klikněte na tlačítko **Správce rozšíření**. Rozšíření TestPublishing by se měla objevit v prostředním podokně a povolit.

3.  Na **nástroje** nabídky, ujistěte se, že se zobrazí příkaz test.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publikování rozšíření do Galerie Visual Studio
 Rozšíření můžete teď publikovat do Galerie Visual Studio.

1.  Ujistěte se, že jste vytvořili na prodejní verzi produktu rozšíření a zda je aktuální.

2.  Ve webovém prohlížeči otevřete [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) webu.

3.  V pravém horním rohu klikněte na tlačítko **SIGN IN**.

4.  K přihlášení pomocí účtu Microsoft. Pokud nemáte účet Microsoft, můžete jeden vytvořit v tomto okamžiku.

5.  Klikněte na tlačítko **nahrát**.

6.  V **krok 1: typ rozšíření**vyberte **nástroj** a potom klikněte na tlačítko **Další**.

7.  V **krok 2: nahrání**, je možné nahrávat přímo do Galerie Visual Studio nebo jednoduše přidejte odkaz na vlastní web. V tomto případě vyberte **chci nahrát nástroj**. **Vybrat ovládací prvek** se zobrazí okno. Klikněte na tlačítko **Procházet** a pak vyberte TestPublish.vsix ve složce \bin\Release projektu. Klikněte na tlačítko **Další**.

8.  V **krok 3: základní informace**, jsou zobrazena pole ze souboru source.extension.vsixmanifest. Vyberte odpovídající **kategorie** a přidejte **značky** k poskytování pomoci uživatelům najít rozšíření. Můžete chtít přidat podrobnější přehled a popis (popis musí být aspoň 280 znaků). Ponechte **typ rozšíření** jako **rozšíření společnosti Microsoft** a **nákladů kategorie** jako **zkušební verze**.

9. Přečtěte si příspěvek smlouvu v dolní části stránky a zkontrolujte **souhlasím**.

10. Klikněte na tlačítko **vytvořit příspěvek**. Zobrazí se stránka, kterou bude mít rozšíření v Galerii Visual Studio se zprávou, že na stránce ještě nebyla publikována.

11. Klikněte na tlačítko **publikovat**.

12. Hledat Galerie sady Visual Studio pro rozšíření. Seznam rozšíření TestPublish by se zobrazit.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Nainstalovat rozšíření z Galerie sady Visual Studio
 Teď, když se publikuje rozšíření, nainstalujte ho v sadě Visual Studio a ho vyzkoušeli.

1.  V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.

2.  Klikněte na tlačítko **Online** a vyhledejte TestPublish. Seznam rozšíření TestPublish by se zobrazit.

3.  Klikněte na tlačítko **Stáhnout**. Po stažení rozšíření, klikněte na tlačítko **nainstalovat**.

4.  K dokončení instalace, restartujte aplikaci Visual Studio.

## <a name="removing-the-extension"></a>Odebírá se rozšíření
 Můžete odebrat rozšíření z Galerie sady Visual Studio a z vašeho počítače.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Odebrat rozšíření z Galerie sady Visual Studio

1.  Otevřít [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) webu.

2.  V pravém horním rohu klikněte na tlačítko **Moje Extenions**. Zobrazí se seznam u možnosti TestPublish.

3.  Klikněte na tlačítko **odstranit**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Odebrat rozšíření z počítače

1.  V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **Správce rozšíření**.

2.  Vyberte TestPublish a potom klikněte na tlačítko **odinstalovat**.

3.  K dokončení odinstalace restartujte aplikaci Visual Studio.
