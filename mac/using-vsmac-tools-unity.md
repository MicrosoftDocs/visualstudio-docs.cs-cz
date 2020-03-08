---
title: Pomocí sady Visual Studio for Mac Tools for Unity
description: Tato příručka popisuje, jak pomocí sady Visual Studio for Mac Tools pro Unity rozšíření
author: therealjohn
ms.author: johmil
ms.date: 12/13/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 4247e5cfb936d79c2b2bea5ac68a16164f0c0ef0
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410525"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Pomocí sady Visual Studio for Mac Tools for Unity

V této části se dozvíte, jak pomocí sady Visual Studio for Mac Tools pro Unity a integrace a funkce pro zvýšení produktivity a jak pomocí sady Visual Studio pro Mac ladicího programu pro vývoj pro Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otevírání skriptů Unity v sadě Visual Studio pro Mac

Jakmile Visual Studio pro Mac [nastavíte jako externí editor skriptů pro Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), otevře se při otevření libovolného skriptu z editoru Unity automatické spuštění nebo přepnutí na Visual Studio pro Mac s vybraným skriptem.

Alternativně můžete Visual Studio pro Mac otevřít bez otevření skriptu v editoru zdrojového kódu tak, že v nabídce **prostředky** v Unity vyberete **otevřít C# projekt** .

![Otevřít projekt C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Přístup k dokumentaci k Unity

Visual Studio for Mac Tools for Unity obsahuje zástupce pro přístup k dokumentaci k rozhraní Unity API. Pokud chcete získat přístup k dokumentaci k rozhraní Unity API z Visual Studio pro Mac, umístěte kurzor na rozhraní Unity API, se kterým chcete získat informace, a stiskněte **⌘ Command +** .

## <a name="intellisense-for-unity-messages"></a>Technologie IntelliSense pro zprávy Unity
Modul Unity vysílá zprávy do skriptů MonoBehaviour a umožňuje vývojářům psát kód, který reaguje na zprávy, jako je například. MouseDown, OnTriggerEnter atd. Vzhledem k tomu, že se nejedná o virtuální metody v základní třídě MonoBehaviour, některé z nich, jako je MonoDevelop, pro zprávy Unity chybí funkce pro dokončování kódu.

Visual Studio for Mac Tools for Unity však rozšiřuje funkčnost technologie IntelliSense pro zprávy Unity. To umožňuje snadno implementovat zprávy Unity skripty třídy MonoBehaviour a pomáhá při učení Unity API. Použití technologie IntelliSense pro zprávy Unity:

1. Umístěte kurzor na nový řádek do těla třídy, která je odvozena z třídy MonoBehaviour.

2. Začněte psát název zprávy Unity, například `OnTriggerEnter`.

3. Po zadání písmen "**ONT**" se zobrazí seznam návrhů technologie IntelliSense.

   ![Používání atributu IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Výběr v seznamu lze změnit třemi způsoby:

   * Pomocí šipek **nahoru** a **dolů** .

   * Po kliknutí myší na požadovanou položku.

   * Pokud budete pokračovat k zadání názvu požadované položky.

5. Technologie IntelliSense můžete vložit vybrané zprávy Unity všechny potřebné parametry včetně:

   * Stisknutím klávesy **TAB**.

   * Stisknutím klávesy **return**.

   * Dvojitým kliknutím na vybranou položku.

   ![Vložit zprávu Unity v IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Přidání nové Unity soubory a složky

I když můžete vždy přidat nové soubory do projektu Unity v editoru Unity, Visual Studio pro Mac umožňuje snadno vytvářet nové skripty Unity, shadery, struktury, výčty a složky z aplikace Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Přidat nový skript jazyka C# třídy MonoBehaviour.

Pokud chcete přidat nový C# skript MonoBehaviour, **klikněte pravým tlačítkem na složku assets (prostředky** ) nebo na jeden z jeho podadresářů na panelu řešení a vyberte **Přidat > nové MonoBehaviour**.

![Přidání nové třídy MonoBehaviour.](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Přidat nový shader pro Unity

Pokud chcete přidat nový shader Unity, **klikněte pravým tlačítkem na složku assets (prostředky** ) nebo na podadresář na panelu řešení a vyberte **Přidat > Nový shader**.

### <a name="add-a-new-folder"></a>Přidat novou složku

Chcete-li přidat novou složku, **klikněte pravým tlačítkem myši na složku assets (prostředky** ) nebo na podadresář na panelu řešení a vyberte **Přidat > Nová složka**.

Tyto doplňky se projeví v okně projektů Unity editor.

### <a name="to-rename-a-file-or-folder"></a>Přejmenování souboru nebo složky
**klikněte pravým tlačítkem myši** na položku, kterou chcete přejmenovat, na panelu řešení a vyberte **Přejmenovat...** .

> [!NOTE]
> Pokud máte nový projekt Unity se žádné skripty a prostředky složka nezobrazí v oblasti řešení v sadě Visual Studio pro Mac, přidejte počáteční skript jazyka C# z v rámci nástroje Unity editor.

## <a name="unity-debugging"></a>Ladění Unity

Projekty Unity můžete ladit pomocí sady Visual Studio pro Mac.

### <a name="start-debugging"></a>Spustit ladění

Spuštění ladění:

1. Připojte Visual Studio k Unity kliknutím na tlačítko **Přehrát** nebo zadejte **příkaz + return**nebo **F5**.

   ![Kliknutím na tlačítko Přehrát v sadě Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Přepněte na Unity a kliknutím na tlačítko **Přehrát** spusťte hru v editoru.

   ![Kliknutím na tlačítko Přehrát v Unity](media/using-vsmac-tools-unity-image6.png)

3. Neopravňují hry v Unity editoru připojeny k sadě Visual Studio budou všechny zarážky, došlo k pozastavení provádění hry a otevřete řádek kódu, kde hru zarážce v sadě Visual Studio pro Mac.

### <a name="start-debugging-in-a-single-step"></a>Spustit ladění v jednom kroku

Spuštění ladění a přehrání editoru Unity můžete provést v jednom kroku přímo z Visual Studio pro Mac výběrem možnosti **připojit k Unity a přehrání** .

![Vybrat připojit k Unity a hrát](media/using-vsmac-tools-unity-image8.png)

### <a name="stop-debugging"></a>Zastavit ladění

Chcete zastavit ladění:

1. Klikněte na tlačítko **zastavit** v Visual Studio pro Mac nebo stiskněte **Shift + Command + Return**.

   ![Klikněte na tlačítko Zastavit ve Visual Studiu](media/using-vsmac-tools-unity-image7.png)

> [!NOTE]
> Pokud jste zahájili ladění pomocí konfigurace **připojit k Unity a Play** , tlačítko **zastavit** také zastaví Unity.

Další informace o ladění v Visual Studio pro Mac najdete v tématu [použití ladicího programu](debugging.md).
