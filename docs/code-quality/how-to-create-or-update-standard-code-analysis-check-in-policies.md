---
title: Vytvořit nebo aktualizovat standardní zásady vracení se změnami analýzy kódu
description: Naučte se, jak zajistit, aby se analýza kódu spouštěla na všech projektech kódu v projektu Azure DevOps. Viz jak nakonfigurovat zásadu vrácení se změnami analýzy kódu projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d46ed89880c41cbcaa6982c386e2ff8f115f8de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860110"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Postupy: Vytváření nebo aktualizace standardních zásad vracení se změnami Analýzy kódu

Můžete vyžadovat, aby se analýza kódu spouštěla na všech projektech kódu v projektu Azure DevOps pomocí zásad vrácení se změnami analýzy kódu. Vyžadování analýzy kódu může zlepšit kvalitu kódu, který je vrácen do základu kódu.

> [!NOTE]
> Tato funkce je k dispozici pouze v případě, že používáte Team Foundation Server.

Zásady vrácení se změnami analýzy kódu jsou nastaveny v nastavení projektu a platí pro každý projekt kódu. Spuštění analýzy kódu je konfigurováno pro projekty kódu v souboru projektu (. xxproj) pro projekt kódu. Spuštění analýzy kódu se provádí v místním počítači. Pokud povolíte zásadu vrácení se změnami analýzy kódu, soubory v projektu kódu, které mají být vráceny se změnami, musí být zkompilovány po poslední úpravě a spuštění analýzy kódu, který obsahuje alespoň pravidla v nastavení projektu musí být provedena v počítači, kde byly provedeny změny.

- Pro spravovaný kód nastavíte zásadu vrácení se změnami zadáním *sady pravidel* , která obsahuje podmnožinu pravidel analýzy kódu.

- V případě kódu C/C++ v aplikaci Visual Studio 2017 verze 15,6 a dřívější zásada vracení se změnami vyžaduje, aby byla spuštěna všechna pravidla analýzy kódu. Můžete přidat direktivy pre-Processor, které zakazují specifická pravidla pro jednotlivé projekty kódu v projektu Azure DevOps. V 15,7 a novějších verzích můžete pomocí **/analyze: RuleSet** určit, která pravidla se mají spustit. Další informace najdete v tématu [použití sad pravidel k určení pravidel C++ ke spuštění](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

Až zadáte zásadu vrácení se změnami pro spravovaný kód, členové týmu mohou synchronizovat nastavení analýzy kódu pro projekty kódu do nastavení zásad projektu Azure DevOps.

## <a name="to-open-the-check-in-policy-editor"></a>Otevření editoru zásad vracení se změnami

1. V Team Explorer klikněte pravým tlačítkem myši na název projektu, přejděte na **nastavení projektu** a pak klikněte na **Správa zdrojového kódu**.

1. V dialogovém okně **Správa zdrojového kódu** vyberte kartu **Zásady vracení se změnami** .

1. Proveďte některou z následujících akcí:

    - Kliknutím na tlačítko **Přidat** vytvořte novou zásadu vrácení se změnami.

    - Pokud chcete zásadu změnit, poklikejte na existující položku **analýzy kódu** v seznamu **typ zásad** .

## <a name="to-set-policy-options"></a>Nastavení možností zásad

Zaškrtněte nebo zrušte zaškrtnutí následujících možností:

|Možnost|Popis|
|------------|-----------------|
|**Vyvynuťte vrácení se změnami tak, aby obsahovalo pouze soubory, které jsou součástí aktuálního řešení.**|Analýza kódu se dá spustit jenom pro soubory zadané v konfiguračních souborech řešení a projektu. Tato zásada zaručuje, že veškerý kód, který je součástí řešení, je analyzován.|
|**Vyhovět analýze kódu C/C++ (/Analyze)**|Vyžaduje, aby všechny projekty C nebo C++ byly sestaveny pomocí možnosti kompilátoru/Analyze pro spuštění analýzy kódu předtím, než mohou být vráceny se změnami.|
|**Vynutila analýzu kódu pro spravovaný kód**|Vyžaduje, aby všechny spravované projekty spouštěly analýzu kódu a sestavování předtím, než mohou být vráceny se změnami.|

## <a name="to-specify-a-managed-rule-set"></a>Určení spravované sady pravidel

V seznamu **Spustit tuto sadu pravidel** použijte jednu z následujících metod:

- Vyberte standardní sadu pravidel společnosti Microsoft.

- Kliknutím vyberte vlastní sadu pravidel **\<Select Rule Set from Source Control...>** . Pak zadejte cestu správy verzí sady pravidel v prohlížeči správy zdrojového kódu. Syntaxe cesty správy verzí je:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Další informace o tom, jak vytvořit a implementovat sadu pravidel pro vlastní vracení se změnami, najdete v tématu [implementace vlastních zásad vrácení se změnami pro spravovaný kód](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Viz také

- [Implementace vlastních zásad vracení zpět se změnami analýzy kódu pro spravovaný kód](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)
