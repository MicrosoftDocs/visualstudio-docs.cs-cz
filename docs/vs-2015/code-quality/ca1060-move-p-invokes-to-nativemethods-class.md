---
title: 'CA1060: Přesuňte P-vyvolá do třídy NativeMethods | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 026f568d71c80af95d2d4bee640dc11d1042713f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913862"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Přesuňte volání nespravovaných kódů do třídy NativeMethods
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Metoda používá platformu vyvolání služby pro přístup k nespravovanému kódu a není členem jedné z **NativeMethods** třídy.

## <a name="rule-description"></a>Popis pravidla
 Metody vyvolání platformy, jako jsou ty, které jsou označeny pomocí <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atribut nebo metody, které jsou definovány pomocí `Declare` – klíčové slovo v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], přístup k nespravovanému kódu. Tyto metody by měly být v jednom z následujících tříd:

- **NativeMethods** – Tato třída nepotlačuje procházení zásobníku oprávnění pro nespravovaný kód. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> nesmí použít pro tuto třídu.) Tato třída je pro metody, které lze použít kdekoli, protože procházení zásobníku se provede.

- **SafeNativeMethods** – Tato třída potlačí procházení zásobníku oprávnění pro nespravovaný kód. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> platí pro tuto třídu.) Tato třída je pro metody, které jsou bezpečné pro každého, kdo k volání. Volající tyto metody není nutné provádět úplnou kontrolu, abyste měli jistotu, že využití je bezpečná, protože jsou neškodné pro jakýkoli volající metody.

- **UnsafeNativeMethods** – Tato třída potlačí procházení zásobníku oprávnění pro nespravovaný kód. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> platí pro tuto třídu.) Tato třída je pro metody, které mohou být nebezpečné. Jakýkoli volající tyto metody musíte provést úplnou kontrolu, abyste měli jistotu, že využití je bezpečná, protože se provede bez procházení zásobníku.

  Tyto třídy jsou deklarovány jako `internal` (`Friend`, v jazyce Visual Basic) a deklarujete soukromého konstruktoru, aby se zabránilo bránit vytváření nových instancí. Metody v těchto tříd by měla být `static` a `internal` (`Shared` a `Friend` v jazyce Visual Basic).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přesuňte metodu na příslušné **NativeMethods** třídy. Pro většinu aplikací, přesun volání nespravovaných kódů do novou třídu s názvem **NativeMethods** je dostatečná.

 Nicméně pokud vyvíjíte knihovny pro použití v jiných aplikacích, měli byste zvážit definování dvě třídy, které jsou volány **SafeNativeMethods** a **UnsafeNativeMethods**. Tyto třídy vypadat podobně jako **NativeMethods** třídy, ale jsou označené pomocí speciální atributu volá **SuppressUnmanagedCodeSecurityAttribute**. Když tento atribut je použit, modul runtime neprovádí úplné zásobníku, abyste měli jistotu, že všichni volající **požadavku na nespravovaný kód** oprávnění. Modul runtime vyhledává obvykle toto oprávnění při spuštění. Protože je kontrola se neprovádí, může výrazně zlepšit výkon volání těchto metod nespravované, ale taky umožňuje kód, který má omezená oprávnění k volání těchto metod.

 Tento atribut by však použít velmi opatrně. Pokud se nesprávně implementuje může mít vážné bezpečnostní důsledky...

 Informace o tom, jak implementovat metodu, najdete v článku **NativeMethods** příkladu **SafeNativeMethods** příkladu a **UnsafeNativeMethods** příklad.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad deklaruje metodu, která poruší toto pravidlo. Chcete-li opravit porušení zásad, **RemoveDirectory** P/Invoke by měla přesunout do vhodné třídy, která slouží k uložení pouze volání nespravovaných kódů.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>Příklad NativeMethods

### <a name="description"></a>Popis
 Vzhledem k tomu, **NativeMethods** třída nemůže být označena jako pomocí **SuppressUnmanagedCodeSecurityAttribute**, volání nespravovaných kódů, které jsou umístěny v něm bude vyžadovat **požadavku na nespravovaný kód** oprávnění. Protože většina aplikací spusťte z místního počítače a spouštět se společně s úplným vztahem důvěryhodnosti, to není obvykle problém. Nicméně, pokud vyvíjíte opakovaně použitelné knihovny, měli byste zvážit definování **SafeNativeMethods** nebo **UnsafeNativeMethods** třídy.

 Následující příklad ukazuje **Interaction.Beep** metodu, která zabalí **MessageBeep** funkce z knihovny user32.dll. **MessageBeep** P/Invoke je umístěn **NativeMethods** třídy.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Příklad SafeNativeMethods

### <a name="description"></a>Popis
 P/Invoke metody, která může být bezpečně vystavena libovolnou aplikaci a všechny vedlejší účinky, které nemají by mělo být uvedeno ve třídě s názvem **SafeNativeMethods**. Nemáte oprávnění k vyžádání a není nutné je potřeba věnovat pozornost mnohem ve kterém jsou volány z.

 Následující příklad ukazuje **Environment.TickCount** vlastnost, která zabalí **GetTickCount** funkce ze souboru kernel32.dll.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Příklad UnsafeNativeMethods

### <a name="description"></a>Popis
 P/Invoke metody, které nejde volat bezpečně a, která by mohla způsobit vedlejší účinky by mělo být uvedeno ve třídě s názvem **UnsafeNativeMethods**. Tyto metody by měly být porovnány přísně, abyste měli jistotu, že nejsou pro uživatele neúmyslnému zveřejnění. Pravidlo [CA2118: revize použití SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) můžou pomoct se to. Metody by případně mají další oprávnění, které je požadováno místo **požadavku na nespravovaný kód** při jejich použití.

 Následující příklad ukazuje **Cursor.Hide** metodu, která zabalí **ShowCursor** funkce z knihovny user32.dll.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Viz také
 [Upozornění ohledně návrhu](../code-quality/design-warnings.md)



