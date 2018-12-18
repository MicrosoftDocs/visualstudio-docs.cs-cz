---
title: Dialogové okno schémata XML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f97bfca4623a826130e68a5399cc2ab86f784cbf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899588"
---
# <a name="xml-schemas-dialog-box"></a>Dialogové okno Schémata XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
**Schémat XML** se používá dialogové okno pro výběr které schématu definice jazyk (XSD) schématu XML pro přidružení k dokumentu XML. Můžete vybrat schéma z mezipaměti schémat nebo zadejte schéma, které se nenachází v mezipaměti. Vybrané schémata jsou považovány za součást této sadě schémat. Sadě schémat se používá technologie IntelliSense a také ověření dokumentu XML.  
  
 Můžete přistupovat **schémat XML** dialogové okno kliknutím **schémata** tlačítka v okně Vlastnosti dokumentu, nebo výběrem **schémata** z **XML** nabídky.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Použití**  
 Vyberte, jak má být použita schématu XML.  
  
- **Automatické**. Toto schéma není používán aktuální dokument, ale je k dispozici pro automatické přidružení. Pokud dokument XML deklaruje obor názvů, který odpovídá `targetNamespace` tohoto schématu schématu bude automaticky přiřazen a je zahrnuté v sadě schémat.  
  
- **Použít tohle schéma**. Toto schéma používá aktuální dokument. Uživatel má explicitně požadována, že kliknete na tomto sloupci používat toto schéma nebo schématu byl automaticky k podle odpovídající `targetNamespace`.  
  
- **Nepoužívat vybraná schémata**. Toto schéma není používán aktuální dokument i v případě schématu nemá odpovídající `targetNamespace`. Toto nastavení může být užitečné při řešení konfliktů, pokud existuje více než jedna verze stejného schématu v mezipaměti schémat nebo řešení.  
  
  **Target Namespace**  
  Zobrazí související s XML schématu cílový obor názvů.  
  
  **Název souboru**  
  Zobrazuje název souboru schématu XML.  
  
  **Add**  
  Otevře **otevřít schéma XSD** dialogové okno, které vám umožní vybrat další schémata pro přidání do sady schémat. Při přidávání schématu do schématu nastavit **použití** nastavena na hodnotu sloupce **použít tohle schéma**.  
  
  **odebrat**  
  Odebere aktuálně vybrané schéma v sadě schémat. Tato operace odebere schéma z mezipaměti schémat v paměti, ale ne ze systému souborů.  
  
## <a name="see-also"></a>Viz také  
 [Součásti editoru XML](../xml-tools/xml-editor-components.md)   
 [Postupy: Výběr schémat XML pro použití](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Mezipaměť schémat](../xml-tools/schema-cache.md)



