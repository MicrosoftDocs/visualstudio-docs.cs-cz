---
title: Příkaz pokyny pro umístění | Dokumentace Microsoftu
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
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1729d4b5e65e60246926c1a3fd25342b10545068
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730999"
---
# <a name="command-placement-guidelines"></a>Pokyny pro umístění příkazu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Osvědčené postupy pro umístění příkazů v prostředí integrovaného vývojového (prostředí IDE) sady Visual Studio se liší v závislosti na velikosti sadu příkazů. Příkazy jsou definovány a podle informací v souborech .vsct umístěn.  
  
## <a name="best-practices-for-all-command-sets"></a>Osvědčené postupy pro všechny sady příkazů  
 Pro každou sadu příkazů postupujte podle následujících pokynů:  
  
-   Příprava grafu příkazovou strukturu předem. Identifikujte příkazy, pole se seznamem, skupiny příkazů a nabídek, které se použijí ve více než jedné oblasti.  
  
-   Příkazy, které se zobrazí ve stejné skupině by měl mít relace.  
  
-   Skupiny, které obsahují pouze jeden příkaz jsou přijatelné.  
  
-   Balíčky, neměli byste přidávat řadu příkazů na stávající nabídky sady Visual Studio. Místo toho by měl vytvořit nabídky a podnabídky k hostování nových příkazů.  
  
-   Když vložíte příkaz na existující nabídky, název příkazu tak, aby objasnili její účel a nebudete se zaměňovat s existující příkazy.  
  
## <a name="best-practices-for-small-command-sets"></a>Osvědčené postupy pro malé příkaz sady  
 Pokud vyvíjíte VSPackage, která má jen několik příkazů, také postupujte podle těchto pokynů:  
  
-   Pokud je to možné, použijte [nadřazeného elementu](../../extensibility/parent-element.md) příkazu, pole se seznamem, skupiny, nebo podřízený nabídky jeho umístění do příslušné skupiny.  
  
-   Tyto skupiny přiřadíte nabídky zobrazí sady VSPackage.  
  
-   Aktivita nadřazená aktivitě podřízené nabídky nebo příkazu musí být [skupinového elementu](../../extensibility/group-element.md). Přiřadit příkazů a nabídek podřízené skupiny a přiřaďte skupiny k nadřazené nabídky.  
  
-   V dalších skupinách můžete umístit příkaz tak, že přidáte [commandplacements – Element](../../extensibility/commandplacements-element.md) části po definici příkazu a následným přidáním do `CommandPlacements Element` [commandplacement – Element](../../extensibility/commandplacement-element.md) pro každý Další skupiny.  
  
## <a name="best-practices-for-large-command-sets"></a>Osvědčené postupy pro příkaz velké sady  
 Pokud vaše VSPackage mnoho příkazů, které se zobrazí v několika kontextech, také dodržujte následující pokyny:  
  
-   Ujistěte se, nabídek, skupiny a příkazy svým nadřazenosti. To znamená, nepřiřazujte `Parent Element` v definici položky.  
  
-   Použití `CommandPlacement Element` položky `CommandPlacements Element` části do nabídek, skupiny a příkazy v jejich nadřazené nabídky a skupiny.  
  
-   V `CommandPlacements` části položky, která naplní dané nabídky nebo skupina by měla být vedle sebe. To pomáhá čitelnost a umožňuje `Priority` snadněji určit pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

