---
title: Klávesové zkratky v Návrhář postupu provádění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f7bc701c4a7009d402c778356a290ce4e129bb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658963"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Klávesové zkratky v návrháři postupu provádění
Ke všem základním funkcím aplikace se [!INCLUDE[wfd1](../includes/wfd1-md.md)] dá dostat z klávesnice.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navigace Návrhář postupu provádění pomocí klávesnice
 Uvnitř jsou [!INCLUDE[vs2010](../includes/vs2010-md.md)] globální zástupci a ladicí zkratky použity pro [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Také byl vytvořen určitý počet [!INCLUDE[wfd2](../includes/wfd2-md.md)] konkrétních klávesových zkratek. V nástroji [!INCLUDE[vs2010](../includes/vs2010-md.md)] lze přemapovat všechny klávesové zkratky. V případě opětovné hostování aplikace se ale tyto klávesové zkratky pevně zakódované.

### <a name="workflow-designer-keyboard-shortcuts"></a>Klávesové zkratky Návrhář postupu provádění
 Následující tabulka shrnuje výchozí klávesové zkratky přiřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] příkazům.

|Zástupce|Účel|
|--------------|-------------|
|CTRL + E, A|Zobrazí nebo skryje návrháře argumentů.|
|CTRL + E, C|Sbalí vybranou aktivitu na místě.|
|CTRL + E, E|Rozšíří vybranou aktivitu na místo.|
|CTRL + E, F|Propojí vybrané aktivity ve vývojovém diagramu.|
|CTRL + E, I|Zobrazí nebo skryje návrháře importu.|
|CTRL + E, M|Přesune fokus klávesnice na další položku v pořadí prvků.|
|CTRL + E, N|Vytvoří novou proměnnou v rozsahu vybrané aktivity (nebo nejbližší).|
|CTRL + E, O|Zobrazí nebo skryje přehledovou mapu.|
|CTRL + E, P|Přejde k nadřazené položce vybrané aktivity. Tím se v navigaci s popisem cesty prochází jedna úroveň a změní se kořenová aktivita na návrhové ploše.|
|CTRL + E, S|Přidá položku s fokusem klávesnice na aktuální výběr.|
|CTRL + E, V|Zobrazí nebo skryje Návrhář proměnných.|
|CTRL + E, X|Rozbalí všechny aktivity v pracovním postupu.|
|CTRL + ALT + F6|Přesune fokus klávesnice z aktuální oblasti uživatelského rozhraní do další oblasti v sekvenci. Pořadí je následující:<br /><br /> 1. navigační panel s popisem cesty<br />2. návrhová plocha<br />3. argumenty/proměnné/Imports Designer, pokud je otevřený<br />4. Shell|

### <a name="flowchart"></a>Vývojový diagram
 Následující seznam obsahuje gesta používaná k vytvoření vývojového diagramu pomocí klávesnice. Stejně jako ve zbývajících částech se [!INCLUDE[wfd2](../includes/wfd2-md.md)] aktivity přidávají na plochu návrháře pomocí zástupců globálních nástrojů, které jsou k dispozici v nástroji [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

- Chcete-li přesunout aktivitu, vyberte aktivitu a pomocí kláves se šipkami ji změňte.

- Chcete-li změnit velikost vývojového diagramu, přesuňte aktivitu za aktuální hranici vývojového diagramu pomocí kláves se šipkami. Automaticky se změní velikost vývojového diagramu.

- Chcete-li nastavit aktivitu jako počáteční uzel, použijte příkaz **Set as StartNode** v místní nabídce.

- Postup připojení aktivit:

  1. Vyberte aktivitu zdroje pomocí klávesy Tabulátor k aktivitě.

  2. Stiskněte kombinaci kláves CTRL + E, M tolikrát, kolikrát je to nutné, aby se fokus klávesnice přesunul na cílovou aktivitu.

  3. Stisknutím kombinace kláves CTRL + E přidejte cílovou aktivitu do výběru.

  4. Stisknutím kombinace kláves CTRL + E, F přidejte konektor ze zdroje do cílového umístění.

  Poznámky týkající se propojení aktivit pomocí klávesnice:

- Můžete vytvořit více připojení současně přidáním dalších aktivit do výběru před stisknutím kombinace kláves CTRL + E, F. Připojení jsou vytvořena v pořadí, ve kterém byly aktivity přidány do výběru.

- Pokud nelze připojit dvojici aktivit, například pokud má zdrojová aktivita již odchozí připojení, budou další připojení mezi aktivitami v rámci výběru stále učiněna, kdykoli to bude možné.

- Když je ve výběru zahrnutý **použitím objektu FlowDecision** a **použitím objektu FlowDecision** nemá žádné odchozí konektory, konektor se umístí na **skutečnou** větev.

### <a name="expression-editing"></a>Úpravy výrazů
 Ve výchozím nastavení se výchozí klávesové zkratky pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Úpravy textu aplikují v editoru výrazů v [!INCLUDE[wfd2](../includes/wfd2-md.md)] nástroji s následujícími omezeními:

- Přemapování klávesových zkratek pro následující příkazy nemá žádný vliv. K přístupu k těmto příkazům při úpravě výrazu lze použít pouze výchozí klávesové zkratky.

    1. Vyjmout

    2. Kopírovat

    3. Vložit

    4. Vybrat vše

    5. Zpět

    6. Opakovat

- Chcete-li změnit mapování klávesových zkratek pro příkazy pro úpravu výrazů uvnitř [!INCLUDE[wfd2](../includes/wfd2-md.md)] v nástroji [!INCLUDE[vs2010](../includes/vs2010-md.md)] , upravte zástupce v [!INCLUDE[wfd2](../includes/wfd2-md.md)] oboru. Změny provedené v oboru textového editoru se automaticky nevztahují na [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Pokud chcete přemapovat zástupce na obou místech, musíte tyto změny použít dvakrát (jednou pro každý obor).