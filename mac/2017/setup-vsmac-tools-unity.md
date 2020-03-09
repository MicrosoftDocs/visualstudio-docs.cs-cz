---
title: Instalační program sady Visual Studio for Mac Tools for Unity
description: Nastavení a instalaci nástrojů Unity pro použití v sadě Visual Studio pro Mac
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d490b4c1268beb4a5ad55263cb186d838005f718
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408540"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Instalace sady Visual Studio for Mac Tools for Unity

Tato část vysvětluje, jak začít používat Visual Studio for Mac Tools pro Unity.

## <a name="install-visual-studio-for-mac"></a>Instalace sady Visual Studio pro Mac

### <a name="unity-bundled-installation"></a>Instalace balíčků Unity

Počínaje Unity 2018.1, Visual Studio for Mac je výchozí C# integrovaného vývojového prostředí (IDE) pro Unity a je součástí Pomocníka pro stáhnout Unity a také nástroj pro instalaci Unity centra. Stáhněte si Unity z [Store.Unity.com](https://store.unity.com/).

Během instalace Ujistěte se, že Visual Studio pro Mac se změnami seznam součástí k instalaci pomocí Unity:

#### <a name="unity-hub"></a>Centrum Unity

![Centrum instalace Unity](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity stáhnout Pomocníka s nastavením

![Instalace Pomocníka s nastavením stáhnout Unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Vyhledat aktualizace sady Visual Studio pro Mac

Verze sady Visual Studio pro Mac součástí instalace Unity nemusí být na nejnovější verzi. Doporučujeme zkontrolovat aktualizace Ujistěte se, že máte přístup k nejnovější nástroje a funkce.

* [Aktualizace Visual Studio pro Mac](update.md)

### <a name="manual-installation"></a>Ruční instalace

Pokud už máte Unity 5.6.1 nebo vyšší, ale nemáte Visual Studio pro Mac, Visual Studio for Mac můžete nainstalovat ručně. Všechny edice sady Visual Studio for Mac jsou spojeny pomocí sady Visual Studio for Mac Tools for Unity, včetně bezplatné Community edition:

* Stáhněte si Visual Studio pro Mac z [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/).
* Visual Studio for Mac Tools for Unity, se během procesu instalace automaticky nainstalují.
* Pro další nápovědu k instalaci postupujte podle pokynů v [Průvodci instalací](/visualstudio/mac/installation/?view=vsmac-2017) nástroje.

> [!NOTE]
> Visual Studio for Mac Tools for Unity vyžaduje Unity verze 5.6.1 nebo vyšší. Pokud chcete ověřit, že je ve vaší verzi Unity povolený Visual Studio Tools for Unity, v nabídce Unity vyberte **o Unity** a vyhledejte text "Microsoft Visual Studio nástrojů pro Unity Enabled" v levém dolním rohu okna.
>
> ![o Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Potvrďte, že je povoleno sady Visual Studio pro Mac rozšíření Tools for Unity

Visual Studio for Mac Tools pro Unity rozšíření by měl být povolen ve výchozím nastavení, můžete to ověřit a zkontrolovat číslo nainstalované verze:

1. V nabídce sady Visual Studio vyberte **rozšíření...** .

   ![Vyberte rozšíření](media/setup-vsmac-tools-unity-image1.png)

2. Rozbalte část vývoj her a potvrďte sady Visual Studio for Mac Tools pro Unity položka.

   ![Položka zobrazení Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurace Unity pomocí sady Visual Studio pro Mac

Počínaje Unity 2018.1, Visual Studio by měl být výchozího externí skript editoru Unity. Můžete to ověřit nebo změnit externí skript editoru sady Visual Studio:

1. V nabídce Unity vyberte **Předvolby.**

   ![Vyberte předvolby](media/setup-vsmac-tools-unity-image4.png)

2. V dialogovém okně Předvolby vyberte kartu **externí nástroje** .

3. V rozevíracím seznamu editoru externích skriptů zvolte možnost **Visual Studio** , pokud je uvedena, jinak vyberte **Procházet...** .

   ![Vyberte Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Pokud jste vybrali možnost **Procházet...** , přejděte do adresáře aplikace a vyberte možnost Visual Studio a klikněte na tlačítko **otevřít**.

   ![Vyberte Otevřít](media/setup-vsmac-tools-unity-image6.png)

5. Po výběru sady Visual Studio v seznamu **editoru externích skriptů** zavřete dialogové okno Předvolby a dokončete proces konfigurace.