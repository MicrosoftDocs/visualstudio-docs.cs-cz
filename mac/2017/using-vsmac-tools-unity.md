---
title: Používání Visual Studio pro Mac nástrojů pro Unity
description: V této příručce se dozvíte, jak používat Visual Studio pro Mac nástroje pro rozšíření Unity.
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315314"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Používání Visual Studio pro Mac nástrojů pro Unity

V této části se dozvíte, jak používat nástroje Visual Studio pro Mac pro integraci a produktivitu Unity a jak používat Visual Studio pro Mac ladicí program pro vývoj Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otevírají se skripty Unity v Visual Studio pro Mac.

Jakmile Visual Studio pro Mac [nastavíte jako externí editor skriptů pro Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), otevře se při otevření libovolného skriptu z editoru Unity automatické spuštění nebo přepnutí na Visual Studio pro Mac s vybraným skriptem.

Alternativně můžete Visual Studio pro Mac otevřít bez otevření skriptu ve zdrojovém editoru tak, že v nabídce **prostředky** v Unity vyberete **Otevřít projekt C#** .

![Otevřít projekt C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Přístup k dokumentaci Unity

Visual Studio pro Mac Tools for Unity obsahují zástupce pro přístup k dokumentaci API Unity. Pokud chcete získat přístup k dokumentaci k rozhraní Unity API z Visual Studio pro Mac, umístěte kurzor na rozhraní Unity API, se kterým chcete získat informace, a stiskněte **⌘ Command +**.

## <a name="intellisense-for-unity-messages"></a>IntelliSense pro zprávy Unity
Modul Unity vysílá zprávy do skriptů MonoBehaviour a umožňuje vývojářům psát kód, který reaguje na zprávy, jako je například. MouseDown, OnTriggerEnter atd. Vzhledem k tomu, že se nejedná o virtuální metody v základní třídě MonoBehaviour, některé z nich, jako je MonoDevelop, pro zprávy Unity chybí funkce pro dokončování kódu.

Visual Studio pro Mac Tools for Unity ale rozšiřují své funkce IntelliSense na zprávy Unity. Díky tomu můžete snadno implementovat zprávy Unity ve skriptech MonoBehaviour a pomáhat s učením rozhraní API Unity. Použití technologie IntelliSense pro zprávy Unity:

1. Umístěte kurzor na nový řádek v těle třídy, která je odvozena z MonoBehaviour.

2. Začněte psát název zprávy Unity, třeba `OnTriggerEnter` .

3. Po zadání písmen "**ONT**" se zobrazí seznam návrhů technologie IntelliSense.

   ![Používání atributu IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Výběr v seznamu lze změnit třemi způsoby:

   * Pomocí šipek **nahoru** a **dolů** .

   * Kliknutím myši na požadovanou položku.

   * Tím, že budete pokračovat zadáním názvu požadované položky.

5. Technologie IntelliSense může vložit vybranou zprávu Unity, včetně nezbytných parametrů:

   * Stisknutím klávesy **TAB**.

   * Stisknutím klávesy **return**.

   * Dvojím kliknutím na vybranou položku.

   ![Vložení zprávy Unity z IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Přidávání nových souborů a složek Unity

I když můžete přidat nové soubory do projektu Unity v editoru Unity, Visual Studio pro Mac umožňuje snadno vytvářet nové skripty, shadery a složky Unity v rámci sady Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Přidání nového skriptu C# MonoBehaviour

Pokud chcete přidat nový skript C# MonoBehaviour, **klikněte pravým tlačítkem na složku assets (prostředky** ) nebo na jeden z jeho podadresářů na panelu řešení a vyberte **Přidat > nový MonoBehaviour**.

![Přidat novou MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Přidat nový shader Unity

Pokud chcete přidat nový shader Unity, **klikněte pravým tlačítkem na složku assets (prostředky** ) nebo na podadresář na panelu řešení a vyberte **Přidat > nový shader**.

### <a name="add-a-new-folder"></a>Přidat novou složku

Chcete-li přidat novou složku, **klikněte pravým tlačítkem myši na složku assets (prostředky** ) nebo na podadresář na panelu řešení a vyberte **Přidat > nová složka**.

Tyto dodatky se projeví v okně projektu v editoru Unity.

### <a name="to-rename-a-file-or-folder"></a>Přejmenování souboru nebo složky
**klikněte pravým tlačítkem myši** na položku, kterou chcete přejmenovat, na panelu řešení a vyberte **Přejmenovat...**.

> [!NOTE]
> Pokud máte nový projekt Unity bez skriptů a Složka assets (prostředky) se na panelu řešení v Visual Studio pro Mac nezobrazuje, přidejte do editoru Unity počáteční skript jazyka C#.

## <a name="unity-debugging"></a>Ladění Unity

Projekty Unity je možné ladit pomocí Visual Studio pro Mac.

### <a name="start-debugging"></a>Spustit ladění

Spuštění ladění:

1. Připojte Visual Studio k Unity kliknutím na tlačítko **Přehrát** nebo zadejte **příkaz + return**nebo **F5**.

   ![Klikněte na tlačítko Přehrát v aplikaci Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Přepněte na Unity a kliknutím na tlačítko **Přehrát** spusťte hru v editoru.

   ![Klikněte na tlačítko Přehrát v Unity](media/using-vsmac-tools-unity-image6.png)

3. Když je hra spuštěna v editoru Unity během připojení k aplikaci Visual Studio, všechny zjištěné zarážky pozastaví provádění hry a zobrazí řádek kódu, kde hra narazí na zarážku v Visual Studio pro Mac.

### <a name="stop-debugging"></a>Zastavit ladění

Zastavení ladění:

1. Klikněte na tlačítko **zastavit** v Visual Studio pro Mac nebo stiskněte **Shift + Command + Return**.

   ![Klikněte na zastavit v aplikaci Visual Studio.](media/using-vsmac-tools-unity-image7.png)

Další informace o ladění v Visual Studio pro Mac najdete v tématu [použití ladicího programu](debugging.md).
