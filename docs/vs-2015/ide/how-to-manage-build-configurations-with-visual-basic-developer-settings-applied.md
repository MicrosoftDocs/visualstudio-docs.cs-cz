---
title: 'Postupy: Správa konfigurací sestavení pomocí Visual Basic použitých nastavení pro vývojáře | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a5f8568edc636955558ec93b55c0aedebf0065d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651826"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Postupy: Správa konfigurací sestavení s použitými nastaveními vývojáře jazyka Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení jsou všechny rozšířené možnosti konfigurace buildu skryté s [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] použitými nastaveními vývojáře. Toto téma vysvětluje, jak tato nastavení ručně povolit.

## <a name="enabling-advanced-build-configurations"></a>Povolení pokročilých konfigurací sestavení
 Ve výchozím nastavení [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] skryje možnost vývojář možnost otevření dialogového okna **Configuration Manager** a seznam **konfigurací** a **platforem** v [Návrháři projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

#### <a name="to-enable-advanced-build-configurations"></a>Postup povolení pokročilých konfigurací sestavení

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. Rozbalte **projekty a řešení**a klikněte na **Obecné**.

    > [!NOTE]
    > **Obecný** uzel je viditelný i v případě, že není zaškrtnuta možnost **Zobrazit všechna nastavení** . Pokud chcete zobrazit všechny dostupné možnosti, klikněte na **Zobrazit všechna nastavení**.

3. Klikněte na **Zobrazit pokročilé konfigurace sestavení**.

4. Klikněte na **OK**.

     V nabídce **sestavení** je nyní k dispozici **Configuration Manager** a seznamy **konfigurací** a **platforem** jsou viditelné v Návrháři projektu.

## <a name="see-also"></a>Viz také
 [Principy](../ide/understanding-build-configurations.md) [kompilování a sestavování](../ide/compiling-and-building-in-visual-studio.md) konfigurací sestavení
