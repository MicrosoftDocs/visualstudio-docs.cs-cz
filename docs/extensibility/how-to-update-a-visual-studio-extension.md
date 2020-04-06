---
title: 'Postup: Aktualizace rozšíření sady Visual Studio | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710652"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Postup: Aktualizace rozšíření sady Visual Studio
Rozšíření sady Visual Studio v systému můžete aktualizovat pomocí **rozšíření a aktualizací** a nainstalovat aktualizovanou verzi. Pokud vytvoříte aktualizovanou verzi rozšíření, můžete ji znamenat jako aktualizovanou zvýšením čísla verze v manifestu VSIX.

 Aktualizace jsou nainstalovány v případě, že manifest `ID` VSIX příchozí rozšíření `Version` má stejné jako nainstalované a vyšší číslo. Pokud `Version` je číslo stejné nebo nižší, balíček nelze nainstalovat. Pokud `ID` se hodnoty neshodují, balíček, který ještě není nainstalován, je rozpoznán jako samostatné rozšíření.

 Chcete-li zabránit konfliktům během vývoje, doporučujeme odinstalovat starší verze probíhajících rozšíření a také odinstalovat nebo zakázat jakékoli jiné potenciálně konfliktní rozšíření.

## <a name="to-update-an-extension-on-your-system"></a>Aktualizace rozšíření v systému

1. V nabídce **Nástroje** klikněte na **Rozšíření a aktualizace**.

2. V levém podokně klepněte na tlačítko **Aktualizace**.

3. V prostředním podokně klikněte na aktualizaci, kterou chcete nainstalovat.

     Číslo verze aktualizovaného rozšíření se zobrazí v pravém podokně spolu s dalšími informacemi.

4. V dolní části pravého podokna klepněte na **tlačítko Aktualizovat**.

## <a name="to-publish-an-update-of-an-extension"></a>Publikování aktualizace rozšíření

1. V sadě Visual Studio otevřete řešení pro rozšíření, které chcete aktualizovat. Proveďte změny.

    > [!IMPORTANT]
    > Nepodepsaná všechna uživatelská rozšíření se neaktualizují automaticky. Vždy byste měli podepsat rozšíření.

2. V **Průzkumníku řešení**, open *source.extension.manifest*.

3. V návrháři manifestu zvyšte hodnotu čísla v poli **Verze.**

4. Uložte řešení a sestavte ho.

5. Nahrajte nový soubor *.vsix* (ve složce\* *\bin\Debug projektu) na web [Webu Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

     Pokud uživatel, který má starší verzi rozšíření, otevře **rozšíření a aktualizace**, zobrazí se nová verze v seznamu **Aktualizace** za předpokladu, že je nástroj nastaven tak, aby automaticky vyhledává aktualizace.

     Automatické kontroly aktualizací v dolní části podokna**Environment** >  **Aktualizace** můžete povolit nebo zakázat (**Povolit/zakázat automatickou detekci dostupných aktualizací**), které mění nastavení **Vyhledat aktualizace** v**rozšířeních a aktualizacích** **prostředí Tools** > **Options** > Environment .

    > [!NOTE]
    > Počínaje aktualizací Visual Studio 2015 Update 2 můžete zadat (v**Environment** > **rozšířeních prostředí a aktualizacích** **nástroje)** > **Options** > zda chcete automatické aktualizace pro rozšíření pro jednotlivé uživatele, všechna rozšíření uživatelů nebo obojí (výchozí nastavení).

## <a name="see-also"></a>Viz také
- [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
