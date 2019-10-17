---
title: Vytváření nebo aktualizace standardních zásad vracení zpět se změnami analýzy kódu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 738bb1bcf14d5b3459f325fe13eb3c4b0119e562
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448964"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Postupy: Vytváření nebo aktualizace standardních zásad vracení se změnami Analýzy kódu

Můžete vyžadovat, aby se analýza kódu spouštěla na všech projektech kódu v projektu Azure DevOps pomocí zásad vrácení se změnami analýzy kódu. Vyžadování analýzy kódu může zlepšit kvalitu kódu, který je vrácen do základu kódu.

> [!NOTE]
> Tato funkce je k dispozici pouze v případě, že používáte Team Foundation Server.

Zásady vrácení se změnami analýzy kódu jsou nastaveny v nastavení projektu a platí pro každý projekt kódu. Spuštění analýzy kódu je konfigurováno pro projekty kódu v souboru projektu (. xxproj) pro projekt kódu. Spuštění analýzy kódu se provádí v místním počítači. Pokud povolíte zásadu vrácení se změnami analýzy kódu, soubory v projektu kódu, které mají být vráceny se změnami, musí být zkompilovány po poslední úpravě a spuštění analýzy kódu, který obsahuje minimálně pravidla v nastavení projektu musí být provedena v počítači, kde změna byl proveden tento počet.

- Pro spravovaný kód nastavíte zásadu vrácení se změnami zadáním *sady pravidel* , která obsahuje podmnožinu pravidel analýzy kódu.

- V případě jazykaC++ C/kódu v aplikaci Visual Studio 2017 verze 15,6 a dřívější zásada vracení se změnami vyžaduje, aby byla spuštěna všechna pravidla analýzy kódu. Můžete přidat direktivy pre-Processor, které zakazují specifická pravidla pro jednotlivé projekty kódu v projektu Azure DevOps. V 15,7 a novějších verzích můžete pomocí **/analyze: RuleSet** určit, která pravidla se mají spustit. Další informace najdete v tématu [použití sad pravidel k určení C++ pravidel ke spuštění](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Až zadáte zásadu vrácení se změnami pro spravovaný kód, členové týmu mohou synchronizovat nastavení analýzy kódu pro projekty kódu do nastavení zásad projektu Azure DevOps.

## <a name="to-open-the-check-in-policy-editor"></a>Otevření editoru zásad vracení se změnami

1. V Team Explorer klikněte pravým tlačítkem myši na název projektu, přejděte na **nastavení projektu**a pak klikněte na **Správa zdrojového kódu**.

1. V dialogovém okně **Správa zdrojového kódu** vyberte kartu **Zásady vracení se změnami** .

1. Proveďte jednu z těchto akcí:

    - Kliknutím na tlačítko **Přidat** vytvořte novou zásadu vrácení se změnami.

    - Pokud chcete zásadu změnit, poklikejte na existující položku **analýzy kódu** v seznamu **typ zásad** .

## <a name="to-set-policy-options"></a>Nastavení možností zásad

Zaškrtněte nebo zrušte zaškrtnutí následujících možností:

|Možnost|Popis|
|------------|-----------------|
|**Vyvynuťte vrácení se změnami tak, aby obsahovalo pouze soubory, které jsou součástí aktuálního řešení.**|Analýza kódu se dá spustit jenom pro soubory zadané v konfiguračních souborech řešení a projektu. Tato zásada zaručuje, že veškerý kód, který je součástí řešení, je analyzován.|
|**Vyhovět analýzeC++ C/kódu (/Analyze)**|Vyžaduje, aby všechny projekty C++ C nebo projekty byly sestaveny pomocí možnosti kompilátoru/Analyze pro spuštění analýzy kódu předtím, než mohou být vráceny se změnami.|
|**Vynutila analýzu kódu pro spravovaný kód**|Vyžaduje, aby všechny spravované projekty spouštěly analýzu kódu a sestavování předtím, než mohou být vráceny se změnami.|

## <a name="to-specify-a-managed-rule-set"></a>Určení spravované sady pravidel

V seznamu **Spustit tuto sadu pravidel** použijte jednu z následujících metod:

- Vyberte standardní sadu pravidel společnosti Microsoft.

- Vyberte sadu vlastních pravidel kliknutím na **\<Select sadu pravidel ze správy zdrojového kódu... >** . Pak zadejte cestu správy verzí sady pravidel v prohlížeči správy zdrojového kódu. Syntaxe cesty správy verzí je:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Další informace o tom, jak vytvořit a implementovat sadu pravidel pro vlastní vracení se změnami, najdete v tématu [implementace vlastních zásad vrácení se změnami pro spravovaný kód](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření a použití zásad vrácení se změnami analýzy kódu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
