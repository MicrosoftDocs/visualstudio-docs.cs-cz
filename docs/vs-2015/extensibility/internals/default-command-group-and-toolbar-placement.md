---
title: Výchozí příkaz, skupiny a umístění nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e91d535697d0e5b9402a7b7eb3bbd4559821c68a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773636"
---
# <a name="default-command-group-and-toolbar-placement"></a>Výchozí umístění příkazů, skupin a panelů nástrojů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sjednocení produktu a stability, uživatelské rozhraní zobrazí určité skupiny příkazů ve výchozím nastavení, a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsahuje definice pro příkazy a skupin. Rozšíření VSPackages můžete taky použít standardní příkazy a skupin.  
  
 Příkaz výchozích spadají do tří kategorií: integrované vývojové prostředí příkazy, příkazy produktu a příkazů editoru.  
  
## <a name="default-ide-commands"></a>Výchozí prostředí IDE příkazy  
 Integrované vývojové prostředí nástrojů výchozí obsahuje příkazy, které sdílí všechny produkty, které jsou obsaženy v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Patří mezi ně příkazy týkající se operací obecného projektu, například **Uložit** příkazu a **přidat položku** příkazu. Rozšíření VSPackages by neměl přidat k nebo odečíst od tento panel nástrojů s jednou výjimkou: Pokud produktu nebo VSPackage přidá nového okna nástroje, pak v okně přidaly do seznamu k dispozici nástroj windows na **zobrazení** nabídky. Vlastní panel nástrojů můžete přidat nové produkty nebo rozšíření VSPackages.  
  
## <a name="default-product-commands"></a>Výchozí produktu příkazy  
 Integrované vývojové prostředí s vlastní výchozí panel nástrojů, která obsahuje důležité a často používané příkazy můžete zadat jednotlivé produkty. Doporučujeme, ale používat stávající nabídky a panely nástrojů, kdykoli je to možné a doplnit je panelů specifické úkoly podle potřeby.  
  
 Pole Priorita pro panel nástrojů určuje jeho umístění řádku. Nulové priority umístí panelu nástrojů na třetím řádku (řádek 3), pod nabídek (řádek 1) a **standardní** nástrojů (řádek 2). Proto se zobrazí na řádku panelů nástrojů (Priorita + 3). Následné panely nástrojů jsou umístěny na stejném řádku, pokud je volného místa; v opačném případě se se automaticky přesouvají na dalším řádku.  
  
## <a name="default-editor-commands"></a>Výchozí Editor příkazy  
 VSPackage, která poskytuje vlastní editor by měla poskytnout výchozí nástrojů, který obsahuje nejdůležitější a často používané příkazy v tomto editoru. Zobrazit panel nástrojů editoru při editoru aktivní a skryt, pokud editor není aktivní. Tento přehled slouží v `VisibilityConstraints Element` souboru .vsct.  
  
 Panely nástrojů editoru by měl být umístěn pod integrované vývojové prostředí a produktu panely nástrojů.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy definované prostředím IDE, nabídky a skupiny](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

