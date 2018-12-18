---
title: Vytvoření nebo aktualizace standardních zásad analýzy kódu vrácení se změnami
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99f0e665e00e614cfcf3f4e285e33345e31ab42b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283233"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Postupy: Vytváření nebo aktualizace standardních zásad vracení se změnami Analýzy kódu

Může vyžadovat spustit analýzu kódu na všechny projekty kódu v projektu Azure DevOps s využitím zásad vrácení se změnami kód analýzy. Vyžadování analýzy kódu můžete zlepšit kvalitu kódu, který je vrácen do báze kódu.

> [!NOTE]
> Tato funkce je dostupná jenom v případě, že používáte Team Foundation Server.

Zásady vrácení se změnami analýzy kódu se nastavují v nastavení projektu a platí pro každý projekt kódu. Spuštění analýzy kódu jsou nakonfigurované pro projekty kódu v souboru projektu (.xxproj) pro projekt kódu. Spuštění analýzy kódu jsou prováděny v místním počítači. Pokud povolíte zásady analýzy kódu vrácení se změnami, musí být zkompilovány soubory v projektu kódu, které se mají být vráceny se změnami po jejich poslední úpravy a analýza kódu spuštění, který obsahuje minimálně pravidla v nastavení projektu musí být provedeny v počítači kde změna byly provedeny s.

- Pro spravovaný kód, nastavíte tak, že určíte zásady vrácení se změnami *sada pravidel, která* , která obsahuje podmnožinu pravidel analýzy kódu.

- Pro kód C/C++ v sadě Visual Studio 2017 verze 15.6 a starší vyžaduje zásady vrácení se změnami, spuštění všech pravidel analýzy kódu. Můžete přidat processoru direktivy zakázat konkrétní pravidla pro jednotlivé projekty v projektu Azure DevOps. Ve verzi 15.7 nebo novější, můžete použít **/ analyze: ruleset** lze určit pravidla, které ke spuštění. Další informace najdete v tématu [pomocí sad pravidel k určování pravidel C++ pro spuštění](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Po zadání zásad vrácení se změnami pro spravovaný kód, členové týmu můžete synchronizovat svoje nastavení analýzy kódu pro projekty kódu mají nastavení zásad Azure DevOps project.

## <a name="to-open-the-check-in-policy-editor"></a>Otevřete editor zásad vrácení se změnami

1. V Průzkumníku týmových projektů, klikněte pravým tlačítkem na název projektu, přejděte na **nastavení projektu**a potom klikněte na tlačítko **správy zdrojových kódů**.

1. V **správy zdrojových kódů** dialogové okno, vyberte **zásad vrácení se změnami** kartu.

1. Proveďte jednu z těchto akcí:

    - Klikněte na tlačítko **přidat** k vytvoření nové zásady vrácení se změnami.

    - Dvakrát klikněte na existující **analýzy kódu** položky v **typ zásad** seznamu můžete změnit zásady.

## <a name="to-set-policy-options"></a>Chcete-li nastavit možnosti zásad

Zaškrtněte nebo zrušte tyto možnosti:

|Možnost|Popis|
|------------|-----------------|
|**Vynuťte vrácení se změnami obsahovat soubory, které jsou součástí aktuálního řešení.**|Analýza kódu lze spustit pouze na soubory zadané v konfiguračních souborech na řešení a projektu. Tato zásada zaručuje, že se analyzují veškerý kód, který je součástí řešení.|
|**Vynutit analýzu kódu C/C++ (/ analyze)**|Vyžaduje sestavit všechny projekty jazyka C nebo C++ pomocí / analyze – možnost kompilátoru pro spuštění analýzy kódu před jejich mohou být vráceny se změnami.|
|**Vynutit analýzu kódu pro spravovaný kód**|Vyžaduje, aby všechny spravované projekty spustit analýzu kódu a sestavení, než se mohou být vráceny se změnami.|

## <a name="to-specify-a-managed-rule-set"></a>Chcete-li určit sada pravidel spravovaná

Z **spustit tuto sadu pravidel** seznamu, použijte jednu z následujících metod:

- Vyberte sadu standardních pravidel společnosti Microsoft.

- Vyberte vlastní pravidlo. Klepnutím na  **\<vybrat sadu pravidel ze správy zdrojového kódu... >**. Zadejte cestu správy verzí sady pravidel, která v prohlížeči zdrojového ovládacího prvku. Syntaxe cestu správy verzí je následující:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Další informace o tom, jak vytvořit a implementovat vlastní zásady vrácení se změnami sady, naleznete v tématu [implementace vlastních zásad vrácení se změnami pro spravovaný kód](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Viz také:

- [Vytváření a používání zásad vrácení se změnami analýzy kódu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)