---
title: Převedení místní funkce na metodu
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "71301693"
---
# <a name="convert-a-local-function-to-a-method"></a>Převedení místní funkce na metodu

Toto refaktoring se vztahuje na:

- C#

**Co:** Převeďte místní funkci na metodu.

**Kdy:** Máte místní funkci, kterou chcete definovat mimo aktuální místní kontext.

**Proč:** Chcete převést místní funkci na metodu, abyste ji mohli volat mimo místní kontext. Můžete chtít převést na metodu, když místní funkce je stále příliš dlouhá. Když definujete funkci v samostatné metodě, váš kód je čitelnější.

## <a name="convert-local-function-to-method-refactoring"></a>Převést místní funkci na metodu refaktoringu

1. Umístěte kurzor do místní funkce.

    ![Převést místní funkci na ukázku kódu metody](media/convert-local-function-to-method.png)

2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

    ![Převést místní funkci na ukázku opravy kódu metody](media/convert-local-function-to-method-codefix.png)

2. Stisknutím klávesy Enter přijměte refaktoring.

    ![Převést místní funkci na ukázku výsledků metody](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře rozhraní .NET](../csharp-developer-productivity.md)
