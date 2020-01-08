---
title: Pomocí sady Visual Studio for Mac Tools for Unity
description: Tato příručka popisuje, jak pomocí sady Visual Studio for Mac Tools pro Unity rozšíření
author: therealjohn
ms.author: johmil
ms.date: 12/13/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 4247e5cfb936d79c2b2bea5ac68a16164f0c0ef0
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75406670"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Pomocí sady Visual Studio for Mac Tools for Unity

V této části se dozvíte, jak pomocí sady Visual Studio for Mac Tools pro Unity a integrace a funkce pro zvýšení produktivity a jak pomocí sady Visual Studio pro Mac ladicího programu pro vývoj pro Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Otevírání skriptů Unity v sadě Visual Studio pro Mac

Jakmile se Visual Studio for Mac [nastavit jako externího skriptu editor pro Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), otevírání všech skriptů z Unity editoru se automaticky spustí nebo přepínače do sady Visual Studio pro Mac, pomocí skriptu pro zvolený otevřete.

Alternativně můžete otevřít Visual Studio for Mac bez skriptů, které jsou otevřeny v editoru zdrojového kódu tak, že vyberete **otevření projektu jazyka C#** z **prostředky** nabídky v Unity.

![Otevřít projekt C#](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Přístup k dokumentaci k Unity

Visual Studio for Mac Tools for Unity obsahuje zástupce pro přístup k dokumentaci k rozhraní Unity API. Chcete-li získat přístup k dokumentaci k rozhraní API Unity v sadě Visual Studio pro Mac, umístěte kurzor přes rozhraní API Unity chcete další informace o a stiskněte klávesu **⌘ příkaz + "** .

## <a name="intellisense-for-unity-messages"></a>Technologie IntelliSense pro zprávy Unity
Modul Unity vysílá zprávy do skriptů MonoBehaviour a umožňuje vývojářům psát kód, který reaguje na zprávy, jako je například. MouseDown, OnTriggerEnter atd. Vzhledem k tomu, že se nejedná o virtuální metody v základní třídě MonoBehaviour, některé z nich, jako je MonoDevelop, pro zprávy Unity chybí funkce pro dokončování kódu.

Visual Studio for Mac Tools for Unity však rozšiřuje funkčnost technologie IntelliSense pro zprávy Unity. To umožňuje snadno implementovat zprávy Unity skripty třídy MonoBehaviour a pomáhá při učení Unity API. Použití technologie IntelliSense pro zprávy Unity:

1. Umístěte kurzor na nový řádek do těla třídy, která je odvozena z třídy MonoBehaviour.

2. Begin zadáním názvu Unity zprávy, jako například `OnTriggerEnter`.

3. Jednou písmena "**ovolit**" jste zadali, se zobrazí v seznamu návrhů IntelliSense.

   ![Používání atributu IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. Výběr v seznamu lze změnit třemi způsoby:

   * S **nahoru** a **dolů** klávesy se šipkami.

   * Po kliknutí myší na požadovanou položku.

   * Pokud budete pokračovat k zadání názvu požadované položky.

5. Technologie IntelliSense můžete vložit vybrané zprávy Unity všechny potřebné parametry včetně:

   * Stisknutím klávesy **kartu**.

   * Stisknutím klávesy **vrátit**.

   * Dvojitým kliknutím na vybranou položku.

   ![Vložit zprávu Unity v IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Přidání nové Unity soubory a složky

I když můžete vždy přidat nové soubory do projektu Unity v editoru Unity, Visual Studio pro Mac umožňuje snadno vytvářet nové skripty Unity, shadery, struktury, výčty a složky z aplikace Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Přidat nový skript jazyka C# třídy MonoBehaviour.

Chcete-li přidat nový skript jazyka C# třídy MonoBehaviour **klikněte pravým tlačítkem na složku prostředků** nebo jeden z jeho podadresářích v oblasti řešení a vyberte **Přidat > Nová třída MonoBehaviour**.

![Přidání nové třídy MonoBehaviour.](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Přidat nový shader pro Unity

Chcete-li přidat nový shader pro Unity **klikněte pravým tlačítkem na složku prostředků** nebo podadresáře v oblasti řešení a vyberte **Přidat > Nová třída Shader**.

### <a name="add-a-new-folder"></a>Přidat novou složku

Chcete-li přidat novou složku **klikněte pravým tlačítkem na složku prostředků** nebo podadresáře v oblasti řešení a vyberte **Přidat > Nová složka**.

Tyto doplňky se projeví v okně projektů Unity editor.

### <a name="to-rename-a-file-or-folder"></a>Přejmenování souboru nebo složky
**Klikněte pravým tlačítkem na** vyplnění na položku, kterou chcete přejmenovat v řešení a vyberte **přejmenování...** .

> [!NOTE]
> Pokud máte nový projekt Unity se žádné skripty a prostředky složka nezobrazí v oblasti řešení v sadě Visual Studio pro Mac, přidejte počáteční skript jazyka C# z v rámci nástroje Unity editor.

## <a name="unity-debugging"></a>Ladění Unity

Projekty Unity můžete ladit pomocí sady Visual Studio pro Mac.

### <a name="start-debugging"></a>Spustit ladění

Spuštění ladění:

1. Připojení sady Visual Studio k Unity po kliknutí **Přehrát** tlačítko nebo typ **příkaz + Return**, nebo **F5**.

   ![Kliknutím na tlačítko Přehrát v sadě Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Přepnout na Unity a kliknutím **Přehrát** tlačítko spustit hry v editoru.

   ![Kliknutím na tlačítko Přehrát v Unity](media/using-vsmac-tools-unity-image6.png)

3. Neopravňují hry v Unity editoru připojeny k sadě Visual Studio budou všechny zarážky, došlo k pozastavení provádění hry a otevřete řádek kódu, kde hru zarážce v sadě Visual Studio pro Mac.

### <a name="start-debugging-in-a-single-step"></a>Spustit ladění v jednom kroku

Spuštění ladění a přehrání editoru Unity můžete provést v jednom kroku přímo z Visual Studio pro Mac výběrem možnosti **připojit k Unity a přehrání** .

![Vybrat připojit k Unity a hrát](media/using-vsmac-tools-unity-image8.png)

### <a name="stop-debugging"></a>Zastavit ladění

Chcete zastavit ladění:

1. Klikněte na tlačítko **Zastavit** v sadě Visual Studio pro Mac, nebo stiskněte tlačítko **Shift + příkaz + Return**.

   ![Klikněte na tlačítko Zastavit ve Visual Studiu](media/using-vsmac-tools-unity-image7.png)

> [!NOTE]
> Pokud jste zahájili ladění pomocí konfigurace **připojit k Unity a Play** , tlačítko **zastavit** také zastaví Unity.

Další informace o ladění v sadě Visual Studio for Mac najdete v tématu [pomocí ladicího programu](debugging.md).
