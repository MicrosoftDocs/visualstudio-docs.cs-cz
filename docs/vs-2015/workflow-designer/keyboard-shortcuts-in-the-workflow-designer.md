---
title: Klávesové zkratky v Návrháři pracovních postupů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 409a39dc889970ee7ad0eff3354fa43de15b7dbe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895337"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Klávesové zkratky v návrháři postupu provádění
Všechny základní funkce [!INCLUDE[wfd1](../includes/wfd1-md.md)] přístupná pomocí klávesnice.  
  
## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navigace pomocí klávesnice návrháře postupu provádění  
 Uvnitř [!INCLUDE[vs2010](../includes/vs2010-md.md)], Globální klávesové zkratky a zkratky ladění pro [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Kromě toho několik [!INCLUDE[wfd2](../includes/wfd2-md.md)] konkrétní klávesové zkratky byly vytvořeny. V [!INCLUDE[vs2010](../includes/vs2010-md.md)], všechny klávesové zkratky můžete přemapovat. V provádění se změněným hostováním aplikací, ale tyto klávesové zkratky jsou pevně zakódované.  
  
### <a name="workflow-designer-keyboard-shortcuts"></a>Klávesové zkratky v Návrháři pracovních postupů  
 Následující tabulka shrnuje výchozí klávesové zkratky, která je přiřazená [!INCLUDE[wfd2](../includes/wfd2-md.md)] příkazy.  
  
|Zástupce|Účel|  
|--------------|-------------|  
|CTRL+E, A|Zobrazí nebo skryje Návrhář argumentů.|  
|CTRL+E, C|Sbalí vybraný aktivity na místě.|  
|CTRL+E, E|Rozbalí vybrané aktivity na místě.|  
|CTRL + E, F|Připojí vybrané aktivity ve vývojovém diagramu.|  
|CTRL + E, MŮŽU|Zobrazí nebo skryje Návrhář importů.|  
|CTRL + E, M|Přesune fokus klávesnice na další položku v pořadí.|  
|CTRL+E, N|Vytvoří novou proměnnou v oboru vybrané aktivity (nebo nejbližší).|  
|CTRL+E, O|Zobrazí nebo skryje přehledovou mapu.|  
|CTRL + E, P|Přejde na nadřazený vybranou aktivitou. To platí nahoru o jednu úroveň ve navigace s popisem cesty a změní kořenové aktivity na plochu návrháře.|  
|CTRL + E, S|Přidá položku s fokus klávesnice do aktuálního výběru.|  
|CTRL+E, V|Zobrazí nebo skryje Návrhář proměnných.|  
|CTRL + E, X|Rozbalí všechny aktivity v pracovním postupu.|  
|CTRL+ALT+F6|Přesune fokus klávesnice z aktuální oblasti uživatelského rozhraní k další oblasti v sekvenci. Pořadí je následujícím způsobem:<br /><br /> 1.  Navigační panel s popisem cesty.<br />2.  Návrhové ploše<br />3.  Návrhář argumentů/proměnné/importů-li otevřít<br />4.  Prostředí|  
  
### <a name="flowchart"></a>Vývojový diagram  
 Následující seznam uvádí gesta použitý k vytvoření vývojový diagram pomocí klávesnice. Stejně jako v zbytek [!INCLUDE[wfd2](../includes/wfd2-md.md)], aktivity jsou přidány na plochu návrháře zkratky globální sada nástrojů, opatřeného [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
- Chcete-li přesunout aktivitu, vyberte aktivitu a pomocí kláves se šipkami do jiného umístění.  
  
- Pokud chcete změnit velikost vývojového diagramu, přesune aktivitu za aktuální ohraničení vývojový diagram pomocí kláves se šipkami. Vývojový diagram se velikost automaticky.  
  
- Chcete-li nastavit aktivitu jako počáteční uzel, použijte **nastavit jako StartNode** příkazu v místní nabídce.  
  
- Připojení aktivity:  
  
  1.  Vyberte zdrojová aktivita tabulátor do aktivity.  
  
  2.  Stiskněte kombinaci kláves CTRL + E, M tolikrát, kolikrát podle potřeby přesuňte fokus klávesnice na cílovou aktivitu.  
  
  3.  Stiskněte kombinaci kláves CTRL + E, S přidat cílová aktivita do výběru.  
  
  4.  Stiskněte kombinaci kláves CTRL + E, F, přidání konektoru ze zdroje do cíle.  
  
  Poznámky o připojení pomocí klávesnice aktivity:  
  
- Několik připojení současně lze vytvořit tak, že přidáte další aktivity do výběru před stisknutím kláves CTRL + E, f Připojení jsou provedeny v pořadí, aktivity byly přidány do výběru.  
  
- Pokud nemůže být připojen pár aktivity, například pokud zdrojová aktivita již má odchozí připojení, další připojení mezi aktivitami ve výběru probíhají stále kdykoli je to možné.  
  
- Když **FlowDecision** je zahrnutá ve výběru a **FlowDecision** nemá žádná odchozí konektory, konektor je umístěn na **True** větve.  
  
### <a name="expression-editing"></a>Úpravy výrazů  
 Ve výchozím nastavení, výchozí klávesové zkratky pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] úprav textu v editoru výrazů v použít [!INCLUDE[wfd2](../includes/wfd2-md.md)], s těmito omezeními:  
  
-   Přemapování klávesové zkratky pro následující příkazy nemá žádný vliv. Výchozí klávesové zkratky můžete použít pouze přístup k těmto příkazům při úpravě výrazu.  
  
    1.  Vyjmout  
  
    2.  Kopírovat  
  
    3.  Vložit  
  
    4.  Vybrat vše  
  
    5.  Vrácení zpět  
  
    6.  Znovu:  
  
-   Přemapování klávesové zkratky pro úpravu příkazů uvnitř výrazu [!INCLUDE[wfd2](../includes/wfd2-md.md)] v [!INCLUDE[vs2010](../includes/vs2010-md.md)], upravte klávesové zkratky v [!INCLUDE[wfd2](../includes/wfd2-md.md)] oboru. Změny provedené v textovém editoru oboru se nevztahují automaticky [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Pokud chcete přemapovat klávesové zkratky na obou místech, musíte použít změny dvakrát (jednou pro každý obor).