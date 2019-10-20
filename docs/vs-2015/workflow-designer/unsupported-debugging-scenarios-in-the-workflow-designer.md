---
title: Nepodporované scénáře ladění v Návrhář postupu provádění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdbe68b416560b85580e3dd30e5f8138b7cd08fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606938"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nepodporované scénáře ladění v návrháři postupu provádění
Návrhář postupu provádění v [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] přidal mnoho nových funkcí, ale stále existují některé scénáře ladění, které nepodporuje. Tento dokument podrobně popisuje nepodporované scénáře ladění Návrhář postupu provádění.

- Po úpravě kódu nelze provádění pokračovat.

- Provádění nemůže pokračovat z libovolného bodu v pracovním postupu (nastavení Next).

- Provádění nemůže pokračovat, dokud se kurzor nedosáhne (spustí se kurzorem).

- Návrháře pracovních postupů nelze použít k ladění pracovních postupů vytvořených v kódu bez použití návrháře.

- Pracovní postupy vytvořené v dřívějších verzích [!INCLUDE[wf](../includes/wf-md.md)] nelze ladit v Návrháři [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

- U propojení mezi aktivitami nebo uzly <xref:System.Activities.Statements.Flowchart> nelze definovat zarážky.

- Schránka není během ladění k dispozici.

- Zarážky nejsou uchovávány, když jsou zkopírovány nebo vloženy aktivity.

- V okně zásobník volání nelze nastavit zarážky pracovního postupu.

- Při vytváření zarážek v návrháři se nepoužijí nastavení **řádku** a **znaku** v dialogovém okně **Nová zarážka** .

- Okno zarážky nebo místní nabídka nepodporuje následující sloupce nebo možnosti ladění pracovního postupu:

  - Podmínka

  - Počet volání

  - Při volání

  - Funkce

  - Data

  - Přihlášení

  - Přejít na zpětný překlad
