---
title: 'Postupy: vytváření nebo aktualizace standardních zásad vracení se změnami analýzy kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8016032a0ea8d1b8c62b2dfc2bbdf72251590c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661781"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Postupy: Vytváření nebo aktualizace standardních zásad vracení se změnami Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vyžadovat, aby se analýza kódu spouštěla na všech projektech kódu v týmovém projektu pomocí zásad vrácení se změnami analýzy kódu. Vyžadování analýzy kódu může zlepšit kvalitu kódu, který je vrácen do základu kódu.

> [!NOTE]
> Tato funkce je k dispozici pouze v případě, že používáte Team Foundation Server.

 Zásady vrácení se změnami analýzy kódu jsou nastaveny v nastavení týmového projektu a platí pro každý projekt kódu v týmovém projektu. Spuštění analýzy kódu je konfigurováno pro projekty kódu v souboru projektu (. xxproj) pro projekt kódu. Spuštění analýzy kódu se provádí v místním počítači. Pokud povolíte zásadu vrácení se změnami analýzy kódu, soubory v projektu kódu, které mají být vráceny se změnami, musí být zkompilovány po poslední úpravě a spuštění analýzy kódu, který obsahuje alespoň pravidla v nastavení týmového projektu musí být provedena v počítači, kde byly provedeny změny.

- Pro spravovaný kód nastavíte zásadu vrácení se změnami zadáním *sady pravidel* , která obsahuje podmnožinu pravidel analýzy kódu.

- V případě kódu C/C++ vyžaduje zásada vracení se změnami, že jsou spuštěna všechna pravidla analýzy kódu. Můžete přidat direktivy před procesory, které zakazují specifická pravidla pro jednotlivé projekty kódu v týmovém projektu.

  Až zadáte zásadu vrácení se změnami pro spravovaný kód, členové týmu mohou synchronizovat nastavení analýzy kódu pro projekty kódu do nastavení zásad pro týmový projekt.

### <a name="to-open-the-check-in-policy-editor"></a>Otevření editoru zásad vracení se změnami

1. V Team Explorer klikněte pravým tlačítkem myši na název týmového projektu, přejděte na položku **nastavení týmového projektu**a klikněte na možnost **Správa zdrojového kódu**.

2. V dialogovém okně **Správa zdrojového kódu** vyberte kartu **Zásady vracení se změnami** .

3. Proveďte jednu z následujících akcí:

    - Kliknutím na tlačítko **Přidat** vytvořte novou zásadu vrácení se změnami.

    - Pokud chcete zásadu změnit, poklikejte na existující položku **analýzy kódu** v seznamu **typ zásad** .

### <a name="to-set-policy-options"></a>Nastavení možností zásad

- Zaškrtněte nebo zrušte zaškrtnutí následujících možností:

    |Možnost|Popis|
    |------------|-----------------|
    |**Vyvynuťte vrácení se změnami tak, aby obsahovalo pouze soubory, které jsou součástí aktuálního řešení.**|Analýza kódu se dá spustit jenom pro soubory zadané v konfiguračních souborech řešení a projektu. Tato zásada zaručuje, že veškerý kód, který je součástí řešení, je analyzován.|
    |**Vyhovět analýze kódu C/C++ (/Analyze)**|Vyžaduje, aby všechny projekty C nebo C++ byly sestaveny pomocí možnosti kompilátoru/Analyze pro spuštění analýzy kódu předtím, než mohou být vráceny se změnami.|
    |**Vynutila analýzu kódu pro spravovaný kód**|Vyžaduje, aby všechny spravované projekty spouštěly analýzu kódu a sestavování předtím, než mohou být vráceny se změnami.|

-

### <a name="to-specify-a-managed-rule-set"></a>Určení spravované sady pravidel

- V seznamu **Spustit tuto sadu pravidel** použijte jednu z následujících metod:

  - Vyberte standardní sadu pravidel společnosti Microsoft.

  - Pokud chcete vybrat vlastní sadu pravidel, klikněte na **\<Select Rule Set from Source Control...>** a potom zadejte cestu správy verzí sady pravidel v prohlížeči správy zdrojového kódu. Syntaxe cesty správy verzí je:

  - **$/** `TeamProjectName` **/** `VersionControlPath`

  - Další informace o tom, jak vytvořit a implementovat sadu pravidel pro vlastní vracení se změnami, najdete v tématu [implementace vlastních zásad vrácení se změnami pro spravovaný kód](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Viz také
 [Vytváření a používání zásad vrácení se změnami Analýzy kódu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
