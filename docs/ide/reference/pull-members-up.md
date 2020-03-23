---
title: Vytáhnout členy nahoru
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d1f7deb7aca1fed7b75b66b17ce2e4d63768a0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969154"
---
# <a name="pull-members-up"></a>Vytáhnout členy nahoru

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje vytáhnout členy až k typu základny.

**Kdy:** Implementovali jste rozhraní a chcete přesunout člena na základní typ.

**Proč:** Vytažení členů umožňuje další implementace rozhraní dědit tyto členy také.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do libovolného člena implementovaného rozhraní.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

   ![Vytáhnout členy nahoru](media/pull-members-up.png)

2. Vyberte **Pull Members až k základnímu typu**.

3. V dialogovém okně vyberte členy, které chcete přidat do vybraného rozhraní.

   ![Vytáhnout člena nahoru](media/pull-members-up-dialog.png)

4. Vyberte **OK**. Vybrané členy jsou vytaženy do rozhraní.

   ![Vytahovat člen dokončen.](media/pull-members-up-completed.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
