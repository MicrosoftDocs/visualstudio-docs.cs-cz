---
title: Vizuální C++ struktury v Návrhář tříd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc9c09c5f92c4193d3d3f58c819f4bc0fc9aaebf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646756"
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury jazyka Visual C++ v návrháři tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrhář tříd podporuje C++ struktury, které jsou deklarovány pomocí klíčového slova `struct`. Následuje příklad:

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 Další informace o použití typu `struct` naleznete v tématu [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).

 Obrazec C++ struktury v diagramu tříd vypadá a funguje jako obrazec třídy, s tím rozdílem, že popisek čte **strukturu** a má čtvercové rohy namísto zaoblených rohů.

|Element kódu|Zobrazení Návrhář tříd|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> Struktura|

## <a name="see-also"></a>Viz také
 [C++ Práce s](../ide/working-with-visual-cpp-code-class-designer.md) [strukturou](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6) [tříd a struktur](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) kódu Visual (návrhář tříd)
