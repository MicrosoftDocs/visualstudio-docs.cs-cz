---
title: Mezinárodní nastavení, prostředí, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ed1ef8941db17c9cc087a80afcad2b4ce982de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650824"
---
# <a name="international-settings-environment-options-dialog-box"></a>Mezinárodní nastavení, prostředí, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stránka mezinárodní nastavení umožňuje změnit výchozí jazyk, pokud máte na počítači nainstalovanou více než jednu jazykovou verzi integrovaného vývojového prostředí (IDE). K tomuto dialogovému oknu se dostanete tak, že v nabídce **nástroje** vyberete **Možnosti** a pak zvolíte **mezinárodní nastavení** ze složky **prostředí** . Pokud se tato stránka v seznamu nezobrazuje, vyberte v dialogovém okně **Možnosti** možnost **Zobrazit všechna nastavení** .

> [!NOTE]
> Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídky, které vidíte, se mohou lišit od toho, co je popsáno v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Jazyk** Obsahuje seznam dostupných jazyků pro nainstalované jazykové verze produktu. Tato možnost není k dispozici, pokud v počítači nemáte nainstalovanou více než jednu jazykovou verzi. Pokud se prostředí sdílí s více jazyky produktů nebo instalací smíšeného jazyka produktů, je výběr jazyka změněn na **stejný jako v systému Microsoft Windows**.

> [!CAUTION]
> V systému, v němž je nainstalováno více jazyků, nejsou tímto nastavením ovlivněny Visual C++ nástroje pro sestavení (cl.exe, link.exe, nmake.exe, bscmake.exe a související soubory). Tyto nástroje používají verzi pro poslední nainstalovaný jazyk a nástroje pro dříve instalovaný jazyk jsou přepsány, protože nástroje Visual C++ Build nepoužívají model satelitní knihovny DLL.

## <a name="see-also"></a>Viz také
 [Dialogové okno Možnosti prostředí](../../ide/reference/environment-options-dialog-box.md)
