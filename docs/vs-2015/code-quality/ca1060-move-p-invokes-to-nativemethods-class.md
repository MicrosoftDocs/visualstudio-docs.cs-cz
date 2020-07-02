---
title: 'CA1060: přesunout P-vyvolání do třídy NativeMethods | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e01ad9fc4fc57917c123404d8863d04240585793
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533429"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Přesuňte volání nespravovaných kódů do třídy NativeMethods
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Metoda používá služby vyvolání platformy pro přístup k nespravovanému kódu a není členem jedné z tříd **NativeMethods** .

## <a name="rule-description"></a>Popis pravidla
 Metody vyvolání platformy, například ty, které jsou označeny pomocí <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributu nebo metody, které jsou definovány pomocí `Declare` klíčového slova v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , přistupuje k nespravovanému kódu. Tyto metody by měly být v jedné z následujících tříd:

- **NativeMethods** – Tato třída potlačí procházení zásobníku pro oprávnění nespravovaného kódu. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> nesmí být použito pro tuto třídu.) Tato třída je určena pro metody, které lze použít kdekoli, protože bude provedeno procházení zásobníku.

- **SafeNativeMethods** – Tato třída potlačí procházení zásobníku pro oprávnění nespravovaného kódu. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> je použito pro tuto třídu.) Tato třída je určena pro metody, které jsou bezpečné pro všechny volání. Volající z těchto metod nejsou vyžadováni k provedení úplné kontroly zabezpečení, aby bylo zajištěno, že je používání bezpečné, protože metody jsou pro libovolného volajícího neškodné.

- **UnsafeNativeMethods** – Tato třída potlačí procházení zásobníku pro oprávnění nespravovaného kódu. ( <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> je použito pro tuto třídu.) Tato třída je určena pro metody, které jsou potenciálně nebezpečné. Každý volající těchto metod musí provést úplnou kontrolu zabezpečení, aby bylo zajištěno, že je použití zabezpečené, protože se neprovede žádné procházení zásobníku.

  Tyto třídy jsou deklarovány jako `internal` ( `Friend` , v Visual Basic) a deklaraci soukromého konstruktoru, aby se zabránilo vytváření nových instancí. Metody v těchto třídách by měly být `static` a `internal` ( `Shared` a `Friend` v Visual Basic).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přesuňte metodu do příslušné třídy **NativeMethods** . Pro většinu aplikací je k dispozici pouze přesun volání nespravovaného volání do nové třídy s názvem **NativeMethods** .

 Pokud však vyvíjíte knihovny pro použití v jiných aplikacích, měli byste zvážit definování dvou dalších tříd, které se nazývají **SafeNativeMethods** a **UnsafeNativeMethods**. Tyto třídy připomínají třídu **NativeMethods** ; jsou však označeny pomocí speciálního atributu s názvem **SuppressUnmanagedCodeSecurityAttribute**. Při použití tohoto atributu modul runtime neprovede kompletní procházení zásobníku, aby bylo zajištěno, že všichni volající **mají oprávnění k** dispozici. Modul runtime obvykle při spuštění kontroluje toto oprávnění. Vzhledem k tomu, že se kontrolu neprovádí, může výrazně zlepšit výkon pro volání těchto nespravovaných metod, ale také umožňuje kód, který má omezená oprávnění k volání těchto metod.

 Tento atribut byste však měli používat s velkou opatrností. Může mít vážné důsledky na zabezpečení, pokud je nesprávně implementován..

 Informace o tom, jak implementovat metody, naleznete v příkladu **NativeMethods** , **SafeNativeMethods** example a **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad deklaruje metodu, která porušuje toto pravidlo. Chcete-li opravit porušení, **RemoveDirectory** volání nespravovaného přístupu do příslušné třídy, která je navržena tak, aby obsahovala pouze volání nespravovaného objektu.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>Příklad NativeMethods

### <a name="description"></a>Popis
 Vzhledem k tomu, že třída **NativeMethods** by neměla být označena pomocí metody **SuppressUnmanagedCodeSecurityAttribute**, volání nespravovaného **přístupu,** která jsou uvedena v této třídě, budou vyžadovat oprávnění k roztřídě. Vzhledem k tomu, že většina aplikací běží z místního počítače a běží společně s úplným vztahem důvěryhodnosti, obvykle se nejedná o problém. Nicméně pokud vyvíjíte opakovaně použitelné knihovny, měli byste zvážit definování třídy **SafeNativeMethods** nebo **UnsafeNativeMethods** .

 Následující příklad ukazuje metodu **interakce. ZvukovýSignál** , která zabalí funkci **MessageBeep** z user32.dll. **MessageBeep** P/Invoke je vložen do třídy **NativeMethods** .

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Příklad SafeNativeMethods

### <a name="description"></a>Popis
 Metody volání, které mohou být bezpečně zpřístupněny všem aplikacím a nemají žádné vedlejší účinky, by měly být umístěny do třídy s názvem **SafeNativeMethods**. Nemáte oprávnění k vyžádání a nemusíte platit mnohem pozor na to, odkud jsou volány.

 Následující příklad ukazuje vlastnost **prostředí. TickCount** , která zabalí funkci **GetTickCount** z kernel32.dll.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Příklad UnsafeNativeMethods

### <a name="description"></a>Popis
 Metody volání, které nelze bezpečně volat a které by mohly způsobit vedlejší účinky, by měly být umístěny ve třídě s názvem **UnsafeNativeMethods**. Tyto metody by měly být přísně kontrolovány, aby se zajistilo, že nejsou uživateli k úmyslu nevystaveni. Pravidlo [CA2118: Zkontrolujte použití SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) , které vám může s tímto. Další možností je, že metody by měly mít jiné oprávnění, které je **požadováno namísto nejenom při jejich** použití.

 Následující příklad ukazuje metodu **Cursor. Hide** , která zabalí funkci **ShowCursor** z user32.dll.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Viz také
 [Upozornění návrhu](../code-quality/design-warnings.md)
