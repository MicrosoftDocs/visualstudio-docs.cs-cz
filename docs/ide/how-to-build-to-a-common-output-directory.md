---
title: 'Postup: Sestavení do společného výstupního adresáře'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1e669789d2117b4bd2ee550dfffb147e46620c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68416746"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Postup: Sestavení do společného výstupního adresáře

Ve výchozím [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nastavení vytvoří každý projekt v řešení ve své vlastní složce uvnitř řešení. Můžete změnit cesty výstupu sestavení vašich projektů vynutit všechny výstupy, které mají být umístěny ve stejné složce.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Umístění všech výstupů řešení do společného adresáře

1. Klikněte na jeden projekt v řešení.

2. V nabídce **Project** klepněte na **položku Vlastnosti**.

3. V závislosti na typu projektu klikněte na kartu **Kompilace** nebo na kartu **Sestavení** a nastavte **výstupní cestu** ke složce, která se použije pro všechny projekty v řešení.

4. Opakujte kroky 1-3 pro všechny projekty v řešení.

## <a name="see-also"></a>Viz také

- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
- [Postup: Změna výstupního adresáře sestavení](../ide/how-to-change-the-build-output-directory.md)