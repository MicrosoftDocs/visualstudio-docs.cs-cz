---
title: Instalační Visual Studio pro Mac nástroje pro Unity
description: Nastavení a instalace nástrojů Unity pro použití v Visual Studio pro Mac
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: cc43dd74fb5427161cb3992394530328129c607c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85949978"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Nastavení Visual Studio pro Mac nástrojů pro Unity

V této části se dozvíte, jak začít s používáním Visual Studio pro Macch nástrojů pro Unity.

## <a name="install-visual-studio-for-mac"></a>Instalace sady Visual Studio pro Mac

### <a name="unity-bundled-installation"></a>Instalace sady Unity

Od Unity 2018,1 je Visual Studio pro Mac výchozí integrované vývojové prostředí (IDE) C# pro Unity a je součástí pomocníka pro stahování Unity a také pomocí nástroje pro instalaci centra Unity. Stáhněte si Unity z [Store.Unity.com](https://store.unity.com/).

Během instalace se ujistěte, že je v seznamu komponent, které se mají nainstalovat pomocí Unity, zaškrtnuté Visual Studio pro Mac.

#### <a name="unity-hub"></a>Centrum Unity

![Instalace centra Unity](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Pomocník pro stahování Unity

![Instalace pomocníka pro stahování Unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Vyhledat aktualizace pro Visual Studio pro Mac

Verze Visual Studio pro Mac zahrnutá v instalaci Unity nemusí být nejnovější. Doporučuje se zkontrolovat aktualizace, abyste měli jistotu, že máte přístup k nejnovějším nástrojům a funkcím.

* [Aktualizace Visual Studio pro Mac](update.md)

### <a name="manual-installation"></a>Ruční instalace

Pokud už máte 5.6.1 Unity nebo vyšší, ale nemáte Visual Studio pro Mac, můžete Visual Studio pro Mac nainstalovat ručně. Všechny edice Visual Studio pro Mac jsou součástí sady Visual Studio pro Mac Tools for Unity, včetně bezplatné edice Community:

* Stáhněte si Visual Studio pro Mac z [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/).
* Visual Studio pro Mac nástroje pro Unity se nainstalují automaticky během procesu instalace.
* Pro další nápovědu k instalaci postupujte podle pokynů v [Průvodci instalací](/visualstudio/mac/installation) nástroje.

> [!NOTE]
> Visual Studio pro Mac Tools for Unity vyžaduje Unity verze 5.6.1 nebo vyšší. Pokud chcete ověřit, že je ve vaší verzi Unity povolený Visual Studio Tools for Unity, v nabídce Unity vyberte **o Unity** a vyhledejte text "Microsoft Visual Studio nástrojů pro Unity Enabled" v levém dolním rohu okna.
>
> ![O Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Potvrďte, že je povolené rozšíření Visual Studio pro Mac Tools for Unity.

I když by ve výchozím nastavení mělo být povolené rozšíření Visual Studio pro Mac Tools for Unity, můžete si ho ověřit a zkontrolovat číslo nainstalované verze:

1. V nabídce sady Visual Studio vyberte **rozšíření...**.

   ![Vybrat rozšíření](media/setup-vsmac-tools-unity-image1.png)

2. Rozbalte část vývoj her a potvrďte položku Visual Studio pro Mac Tools for Unity.

   ![Zobrazit položku Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurace Unity pro použití s Visual Studio pro Mac

Od Unity 2018,1 by měl být Visual Studio výchozím editorem externích skriptů v Unity. Můžete to potvrdit nebo změnit externí editor skriptu na Visual Studio:

1. V nabídce Unity vyberte **Předvolby.**

   ![Vybrat předvolby](media/setup-vsmac-tools-unity-image4.png)

2. V dialogovém okně Předvolby vyberte kartu **externí nástroje** .

3. V rozevíracím seznamu editoru externích skriptů zvolte možnost **Visual Studio** , pokud je uvedena, jinak vyberte **Procházet...**.

   ![Vybrat Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Pokud jste vybrali možnost **Procházet...** , přejděte do adresáře aplikace a vyberte možnost Visual Studio a klikněte na tlačítko **otevřít**.

   ![Vyberte otevřít.](media/setup-vsmac-tools-unity-image6.png)

5. Po výběru sady Visual Studio v seznamu **editoru externích skriptů** zavřete dialogové okno Předvolby a dokončete proces konfigurace.