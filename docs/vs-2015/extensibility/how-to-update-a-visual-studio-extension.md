---
title: Aktualizovat rozšíření | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d1464cdd2be79cd93a3e98bcf8769e8f4b8b89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837247"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Postupy: Aktualizace rozšíření sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšíření sady Visual Studio můžete v systému aktualizovat pomocí **rozšíření a aktualizací** pro instalaci aktualizované verze. Pokud vytvoříte aktualizovanou verzi rozšíření, můžete ji označit jako aktualizovanou zvýšením čísla verze v manifestu VSIX.

 Aktualizace se instalují, když manifest VSIX příchozího rozšíření je stejný `ID` jako nainstalovaný a vyšší `Version` číslo. Pokud `Version` je číslo stejné nebo nižší, balíček nejde nainstalovat. Pokud se `ID` hodnoty neshodují, bude balíček, který ještě není nainstalovaný, rozpoznaný jako samostatná přípona.

 Aby se zabránilo konfliktům při vývoji, doporučujeme odinstalovat předchozí verze rozšíření a také odinstalovat nebo zakázat jakákoli další potenciálně konfliktní rozšíření.

### <a name="to-update-an-extension-on-your-system"></a>Aktualizace rozšíření v systému

1. V nabídce **Nástroje** klikněte na **Rozšíření a aktualizace**.

2. V levém podokně klikněte na **aktualizace**.

3. V prostředním podokně klikněte na aktualizaci, kterou chcete nainstalovat.

     Číslo verze aktualizovaného rozšíření se zobrazí v pravém podokně spolu s dalšími informacemi.

4. V dolní části pravého podokna klikněte na **aktualizovat**.

### <a name="to-publish-an-update-of-an-extension"></a>Publikování aktualizace rozšíření

1. V aplikaci Visual Studio otevřete řešení pro rozšíření, které chcete aktualizovat. Proveďte změny.

    > [!IMPORTANT]
    > Nepodepsaná všechna uživatelská rozšíření se automaticky neaktualizují. Vaše rozšíření byste měli vždycky podepisovat.

2. V **Průzkumník řešení**otevřete source. extension. manifest.

3. V Návrháři manifestu zvyšte hodnotu čísla v poli **verze** .

4. Uložte řešení a sestavte ho.

5. Nahrajte nový soubor. vsix (ve složce \bin\Debug\ projektu) na web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

     Když uživatel, který má starší verzi rozšíření, otevře **rozšíření a aktualizace**, zobrazí se nová verze v seznamu **aktualizace** za předpokladu, že nástroj je nastaven tak, aby automaticky hledal aktualizace.

     Můžete povolit nebo zakázat automatickou kontrolu aktualizací v dolní části podokna **aktualizace** (**Povolit/zakázat automatickou detekci dostupných aktualizací**), která změní nastavení **Vyhledat aktualizace** v **nabídce Nástroje/možnosti/prostředí/rozšíření a aktualizace**.

    > [!NOTE]
    > Počínaje verzí Visual Studio 2015 Update 2 můžete určit (v části **Nástroje/možnosti/prostředí/rozšíření a aktualizace**), jestli chcete automatické aktualizace pro jednotlivá uživatelská rozšíření, všechna uživatelská rozšíření nebo obojí (výchozí nastavení).

## <a name="see-also"></a>Viz také
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md) [hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
