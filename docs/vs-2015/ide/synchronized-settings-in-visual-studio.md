---
title: Synchronizovaná nastavení
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6459b6f65fd1e29fbadb01f6aa2fc51520b726b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646817"
---
# <a name="synchronized-settings-in-visual-studio"></a>Synchronizovaná nastavení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použijete-li stejný účet přizpůsobení pro přihlášení k aplikaci Visual Studio na více počítačích, ve výchozím nastavení jsou nastavení synchronizována na všech počítačích.

## <a name="synchronized-settings"></a>Synchronizovaná nastavení
 Ve výchozím nastavení se synchronizují následující nastavení.

- Nastavení vývoje (při prvním spuštění sady Visual Studio musíte vybrat sadu nastavení), ale výběr můžete kdykoli změnit. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)

- Na stránkách **Možnosti nástrojů &#124;**  se nacházejí tyto možnosti:

  - Nastavení **malých a velkých** písmen na panelu nabídek, na stránce **prostředí**, **Obecné** možnosti

  - Všechna nastavení na stránce možností **prostředí**, **písma a barvy**

  - Všechny klávesové zkratky, na stránce možnosti **prostředí**, **klávesnice**

  - Všechna nastavení na stránce **prostředí, karty a možnosti systému Windows**

  - Všechna nastavení na stránce možnosti **prostředí**, **spuštění**

  - Všechna nastavení na stránkách možností **textového editoru**

- Všechna nastavení na stránkách možností Návrhář XAML

- Aliasy příkazů definované uživatelem Další informace o tom, jak definovat aliasy příkazů, naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Uživatelsky definované rozložení oken v **okně &#124; spravovat stránku rozložení oken**

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Vypnutí synchronizovaných nastavení pro určitý počítač
 Synchronizovaná nastavení pro Visual Studio jsou ve výchozím nastavení zapnutá. Synchronizovaná nastavení v počítači můžete vypnout tak, že na stránce **Nástroje možnosti &#124; &#124; nástrojů v &#124; prostředí zvolíte nastavení synchronizované** a zrušíte zaškrtnutí políčka.  Pokud se například rozhodnete, že nechcete synchronizovat nastavení sady Visual Studio na počítači A, žádné změny nastavení provedené v počítači A se nezobrazí v počítači B nebo v počítači C. počítač B a C budou nadále synchronizovány navzájem, ale nikoli pomocí počítače A.

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Synchronizace nastavení napříč produkty a edicemi řady Visual Studio
 Nastavení lze synchronizovat v jakékoli edici sady Visual Studio 2015, včetně edice Express a Community. Nastavení jsou také synchronizována v produktech řady Visual Studio, jako je například Blend. Každý z těchto rodinných produktů však může mít vlastní nastavení, která nejsou sdílena se sadou Visual Studio. Například nastavení specifická pro Blend v počítači A budou sdílena s nástrojem Blend v počítači B, ale ne se sadou Visual Studio v počítači A nebo B.

> [!WARNING]
> Nastavení nejsou synchronizovaná mezi Visual Studio 2013 a Visual Studio 2015. Při prvním otevření sady Visual Studio 2015 se migrují nastavení z Visual Studio 2013, ale nelze je migrovat zpět na Visual Studio 2013.

## <a name="see-also"></a>Viz také
 [Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md)
