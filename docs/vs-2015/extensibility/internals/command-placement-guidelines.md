---
title: Pokyny pro umístění příkazů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d88a477403c98ff11c5f7303b55f5eb713b668c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195098"
---
# <a name="command-placement-guidelines"></a>Pokyny pro umístění příkazu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Osvědčené postupy pro umístění příkazů v integrovaném vývojovém prostředí (IDE) sady Visual Studio se liší v závislosti na velikosti sady příkazů. Příkazy jsou definovány a umístěny podle informací v souborech. vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Osvědčené postupy pro všechny sady příkazů  
 Pro každou sadu příkazů postupujte podle těchto pokynů:  
  
- Připravte graf struktury příkazu předem. Identifikujte příkazy, pole se seznamem, skupiny příkazů a místní nabídky, které budou použity ve více než jednom umístění.  
  
- Příkazy, které se zobrazují ve stejné skupině, by měly souviset.  
  
- Přijatelné jsou skupiny, které obsahují jenom jeden příkaz.  
  
- Balíčky by neměly přidávat spoustu příkazů do stávajících nabídek sady Visual Studio. Místo toho by se měly vytvořit nabídky nebo podnabídky pro hostování nových příkazů.  
  
- Když zadáte příkaz do existující nabídky, pojmenujte příkaz tak, aby jeho účel byl jasný a nebude zaměněn s existujícími příkazy.  
  
## <a name="best-practices-for-small-command-sets"></a>Osvědčené postupy pro malé sady příkazů  
 Pokud vyvíjíte VSPackage, který obsahuje pouze několik příkazů, postupujte také podle následujících pokynů:  
  
- Pokud je to možné, použijte [nadřazený element](../../extensibility/parent-element.md) příkazu, pole se seznamem, skupinu nebo podřízenou nabídku k umístění do příslušné skupiny.  
  
- Přiřaďte tyto skupiny k nabídkám, které zobrazuje VSPackage.  
  
- Nadřazený objekt podřízené nabídky nebo příkazu musí být [prvek skupiny](../../extensibility/group-element.md). Přiřaďte příkazy a podřízené nabídky do skupin a potom přiřaďte skupiny k nadřazeným nabídkám.  
  
- Příkaz lze vložit do dalších skupin přidáním oddílu [prvku CommandPlacements](../../extensibility/commandplacements-element.md) po definování příkazu a následně přidáním do `CommandPlacements Element` [prvku CommandPlacement](../../extensibility/commandplacement-element.md) pro každou další skupinu.  
  
## <a name="best-practices-for-large-command-sets"></a>Osvědčené postupy pro velké sady příkazů  
 Pokud VSPackage bude mít mnoho příkazů, které se zobrazí v několika kontextech, postupujte také podle těchto pokynů:  
  
- Vytváření nabídek, skupin a příkazů pro samoobslužné vytváření nadřazených objektů. To znamená, že nepřiřazujte do `Parent Element` definice položky.  
  
- Pomocí `CommandPlacement Element` záznamů v `CommandPlacements Element` části můžete vkládat nabídky, skupiny a příkazy do svých nadřazených nabídek a skupin.  
  
- `CommandPlacements`Položky, které naplňují danou nabídku nebo skupinu, by měly být v sekci sousedící. Tato pomůcka pomáhá číst a usnadňuje `Priority` určování pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
