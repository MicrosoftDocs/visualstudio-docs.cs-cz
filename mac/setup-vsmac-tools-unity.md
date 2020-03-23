---
title: Nastavení visual studia pro nástroje Mac pro jednotu
description: Nastavení a instalace nástrojů Unity pro použití ve Visual Studiu for Mac
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 1981141a01848dc7fac09913548f205a04ce618e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79303342"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Nastavení Visual Studia pro Mac Nástroje pro jednotu

Tato část vysvětluje, jak začít používat Visual Studio for Mac Tools for Unity.

## <a name="install-visual-studio-for-mac"></a>Instalace sady Visual Studio pro Mac

### <a name="unity-bundled-installation"></a>Unity přibalená instalace

Počínaje Unity 2018.1, Visual Studio pro Mac je výchozí C# integrované vývojové prostředí (IDE) pro unity a je součástí Unity Download Assistant, stejně jako nástroj pro instalaci Unity Hub. Stáhnout Unity z [store.unity.com](https://store.unity.com/).

Během instalace se ujistěte, že visual studio pro Mac je zaškrtnuto v seznamu součástí pro instalaci pomocí Unity:

#### <a name="unity-hub"></a>Centrum Unity

![instalace rozbočovače unity](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Asistent stahování Unity

![unity download asistent instalace](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Kontrola aktualizací Visual Studia pro Mac

Verze Visual Studia pro Mac, která je součástí instalace Unity, nemusí být nejnovější. Doporučujeme vyhledat aktualizace, abyste měli přístup k nejnovějším nástrojům a funkcím.

* [Aktualizace Visual Studia pro Mac](update.md)

### <a name="manual-installation"></a>Ruční instalace

Pokud už máte Unity 5.6.1 nebo vyšší, ale nemáte Visual Studio pro Mac, můžete nainstalovat Visual Studio pro Mac ručně. Všechny edice Visual Studia for Mac jsou dodávány s Visual Studio pro Mac Tools for Unity, včetně bezplatné verze Community:

* Stáhněte si Visual Studio pro Mac z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
* Visual Studio for Mac Tools for Unity se instaluje automaticky během procesu instalace.
* Další nápovědu k instalaci naleznete v návodu k [instalaci.](/visualstudio/mac/installation)

> [!NOTE]
> Visual Studio for Mac Tools for Unity vyžaduje Unity verze 5.6.1 nebo vyšší. Chcete-li ověřit, že Nástroje sady Visual Studio pro jednotu jsou povoleny ve vaší verzi Unity, vyberte **o jednotě** z nabídky Unity a vyhledejte text "Microsoft Visual Studio Tools for Unity povoleno" v levém dolním rohu dialogového okna.
>
> ![O jednotě](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Zkontrolujte, zda je povoleno rozšíření Visual Studio for Mac Tools for Unity

Zatímco rozšíření Visual Studio for Mac Tools for Unity by mělo být ve výchozím nastavení povoleno, můžete to potvrdit a zkontrolovat nainstalované číslo verze:

1. V nabídce Visual Studio vyberte **Rozšíření...**.

   ![Vybrat rozšíření](media/setup-vsmac-tools-unity-image1.png)

2. Rozbalte část Vývoj her a potvrďte položku Visual Studio for Mac Tools for Unity.

   ![Zobrazit položku jednoty](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurace unity pro použití s Visual Studio pro Mac

Počínaje Unity 2018.1, Visual Studio by měl být výchozí externí editor skriptů v Unity. Můžete to potvrdit nebo změnit externí editor skriptů na Visual Studio:

1. V nabídce Unity vyberte **Předvolby.**

   ![Vybrat předvolby](media/setup-vsmac-tools-unity-image4.png)

2. V dialogovém okně Předvolby vyberte kartu **Externí nástroje.**

3. V rozevíracím seznamu Externí editor skriptů zvolte **Visual Studio,** pokud je v seznamu, jinak vyberte **Procházet...**.

   ![Výběr sady Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Pokud byla vybrána **možnost Procházet...** byla vybrána, přejděte do adresáře Aplikace a vyberte Visual Studio a klepněte na tlačítko **Otevřít**.

   ![Vybrat otevřít](media/setup-vsmac-tools-unity-image6.png)

5. Po výběru sady Visual Studio v seznamu **Editor externího skriptu** zavřete dialogové okno Předvolby a dokončete proces konfigurace.