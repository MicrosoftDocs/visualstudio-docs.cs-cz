---
title: Nepodporované scénáře ladění
description: Přečtěte si o nepodporovaných scénářích ladění v Návrhář postupu provádění, například "spuštění nelze pokračovat po úpravě kódu."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 4e98e2a75905f4c0a4c007691a99961dbcf1477c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996263"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nepodporované scénáře ladění v návrháři postupu provádění

Návrhář postupu provádění nepodporuje následující scénáře ladění:

- Po úpravě kódu nelze provádění pokračovat.

- Provádění nemůže pokračovat z libovolného bodu v pracovním postupu (nastavení Next).

- Provádění nemůže pokračovat, dokud se kurzor nedosáhne (spustí se kurzorem).

- Návrháře pracovních postupů nelze použít k ladění pracovních postupů vytvořených v kódu bez použití návrháře.

- Pracovní postupy vytvořené v dřívějších verzích programovací model Windows Workflow Foundation (WF) se nedají ladit v .NET Framework 4 nebo novějším.

- U propojení mezi aktivitami nebo uzly nelze definovat zarážky <xref:System.Activities.Statements.Flowchart> .

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

  - Proces

  - Přejít na zpětný překlad
