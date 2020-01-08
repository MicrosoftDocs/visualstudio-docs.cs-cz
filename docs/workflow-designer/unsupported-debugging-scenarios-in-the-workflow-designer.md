---
title: Nepodporované scénáře ladění v návrháři postupu provádění
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 77d1318dbdb23516902523e9c7865dad781cb06b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593034"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nepodporované scénáře ladění v návrháři postupu provádění

Návrhář postupu provádění nepodporuje následující scénáře ladění:

- Po úpravě kódu nelze provádění pokračovat.

- Provádění nemůže pokračovat z libovolného bodu v pracovním postupu (nastavení Next).

- Provádění nemůže pokračovat, dokud se kurzor nedosáhne (spustí se kurzorem).

- Návrháře pracovních postupů nelze použít k ladění pracovních postupů vytvořených v kódu bez použití návrháře.

- Pracovní postupy vytvořené v dřívějších verzích programovací model Windows Workflow Foundation (WF) se nedají ladit v .NET Framework 4 nebo novějším.

- U propojení mezi aktivitami nebo uzly <xref:System.Activities.Statements.Flowchart> nelze definovat zarážky.

- Schránka není během ladění k dispozici.

- Zarážky nejsou uchovávány, když jsou zkopírovány nebo vloženy aktivity.

- V okně zásobník volání nelze nastavit zarážky pracovního postupu.

- Při vytváření zarážek v návrháři se nepoužijí nastavení **řádku** a **znaku** v dialogovém okně **Nová zarážka** .

- Okno zarážky nebo místní nabídka nepodporuje následující sloupce nebo možnosti ladění pracovního postupu:

  - Podmínka

  - Počet přístupů

  - Při volání

  - Funkce

  - Datové

  - Proces

  - Přejít na zpětný překlad
