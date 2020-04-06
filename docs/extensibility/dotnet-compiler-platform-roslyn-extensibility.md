---
title: Rozšiřitelnost kompilátoru .NET (&quot;Roslyn&quot;) Rozšiřitelnost | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712081"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Rozšiřitelnost platformy&quot;kompilátoru .NET (Roslyn)&quot;
Hlavním posláním platformy kompilátoru .NET ("Roslyn") je otevření kompilátorů jazyka C# a Visual Basic a umožnění nástrojům a vývojářům sdílet bohaté informace, které mají kompilátory o programech. Nástroje pro analýzu kódu zlepšují kvalitu kódu a generátory kódu pomáhají při konstrukci aplikací. Jak se nástroje zpřesňují, potřebují přístup k více a více znalostem hlubokého kódu, které mají pouze kompilátory. Namísto neprůhledných překladačů (zdrojový kód a kód objektu out), kompilátory Roslyn nabízejí api, které můžete použít pro úlohy související s kódem ve vašich nástrojích a aplikacích.

 Nejlepší na tom je, že kompilátory Roslyn, jejich api, ukázky a návody a skutečné nástroje postavené na těchto apich jsou plně open source na [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Prosím, přejděte na stránky OSS se dozvědět více a začít s Roslyn. Najdete odkazy získat nejnovější c# a visual basic funkce, které můžete použít jako koncový uživatel, stejně jako odkazy, jak začít jako tvůrce nástrojů využití roslyn rozhraní API.

## <a name="see-also"></a>Viz také
- [Začínáme s analyzátory Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
