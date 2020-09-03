---
title: 'CA2000: uvolnit objekty před ztrátou oboru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e3de3246980ead0b20d471321a9696451aed81ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534768"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Uvolňujte objekty před ztrátou oboru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Kategorie|Microsoft.Reliability|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Je vytvořen místní objekt typu <xref:System.IDisposable>, který však není uvolněn před tím, než jsou všechny odkazy na objekt mimo rozsah.

## <a name="rule-description"></a>Popis pravidla
 Pokud není uvolnitelný objekt explicitně odstraněn před tím, než jsou všechny odkazy mimo rozsah, bude objekt odstraněn v době, kdy bude systémem uvolňování paměti spuštěna finalizační metoda objektu. Vzhledem k tomu, že může dojít k mimořádné události, která zabrání spuštění finalizační metody objektu, měl by namísto toho být objekt explicitně odstraněn.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li vyřešit porušení tohoto pravidla, musíte zavolat na objekt metodu <xref:System.IDisposable.Dispose%2A> před tím, než jsou všechny odkazy na něj mimo rozsah.

 Všimněte si, že příkaz `using` (`Using` v rámci [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) můžete použít pro zabalení objektů, které implementují vzor `IDisposable`. Objekty, které jsou zabaleny tímto způsobem, budou automaticky odstraněny při uzavření bloku `using`.

 Níže jsou uvedeny některé situace, ve kterých příkaz using nepostačuje pro ochranu objektů IDisposable a může způsobit výskyt upozornění CA2000.

- Vracení uvolnitelného objektu vyžaduje, aby byl objekt zkonstruován v rámci bloku try/finally mimo blok using.

- Inicializace členů uvolnitelného objektu by neměla být provedena v rámci konstruktoru příkazu using.

- Vnořené konstruktory, které jsou chráněny pouze jednou obslužnou rutinou výjimky. Příklad:

    ```
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     způsobí výskyt upozornění CA2000, protože selhání vytvoření objektu StreamReader může vést k tomu, že objekt FileStream nebude nikdy uzavřen.

- Dynamické objekty by k implementaci vzoru odstranění objektů IDisposable měly používat stínový objekt.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění tohoto pravidla, pokud jste volali metodu na objekt, který volá metodu `Dispose`, jako například <xref:System.IO.Stream.Close%2A>, nebo pokud metoda, která vyvolala upozornění, vrátí objekt IDisposable zabalující objekt.

## <a name="related-rules"></a>Související pravidla
 [CA2213: Uvolnitelná pole by měla být uvolněna](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: Neuvolňujte objekty několikrát](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Příklad
 Při implementaci metody, která vrací uvolnitelný objekt, je zapotřebí použít blok try/finally bez použití bloku catch. Jedině tak zajistíte, aby byl objekt uvolněn. Pomocí bloku try/finally lze povolit vyvolání výjimek v místě selhání a zajistit, aby byl objekt uvolněn.

 V metodě OpenPort1 se volání za účelem otevření objektu ISerializable SerialPort nebo volání metody SomeMethod nemusí zdařit. V této implementaci je vyvoláno upozornění CA2000.

 V metodě OpenPort2 jsou deklarovány dva objekty SerialPort a jsou nastaveny na hodnotu null:

- `tempPort`, který slouží k otestování úspěšné operace metody.

- `port`, který se používá pro návratovou hodnotu metody.

  Objekt `tempPort` je vytvořen a otevřen v rámci bloku `try` a jakákoli jiná požadovaná činnost je vykonána v rámci stejného bloku `try`. Na konci bloku `try` je otevřený port přiřazen objektu `port`, který bude vrácen, a objekt `tempPort` je nastaven na hodnotu `null`.

  Blok `finally` ověřuje hodnotu `tempPort`. Pokud hodnota není null, operace se v rámci metody nezdařila a blok `tempPort` je uzavřen, aby bylo možné zajistit uvolnění jakýchkoli prostředků. Vrácený objekt portu bude obsahovat otevřený objekt SerialPort, pokud byly operace metody úspěšné, nebo bude mít hodnotu null, pokud se operace nezdaří.

  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]

## <a name="example"></a>Příklad
 Ve výchozím nastavení jsou všechny aritmetické operátory kompilátoru [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ověřovány v rámci přetečení. Proto může jakákoli aritmetická operace jazyka Visual Basic vyvolat výjimku <xref:System.OverflowException>. To může vést k neočekávaným případům porušování pravidel, jako je například CA2000. Například následující funkce CreateReader1 ohlásí porušení pravidla CA2000, protože kompilátor jazyka Visual Basic generuje dodatečnou instrukci kontroly přetečení, jež může vyvolat výjimku, která může způsobit, že StreamReader nebude odstraněn.

 Chcete-li tento problém vyřešit, můžete zakázat generování kontrol přetečení kompilátorem jazyka Visual Basic v rámci projektu nebo upravit kód tak, jak je tomu v následující funkci CreateReader2.

 Chcete-li zakázat generování kontrol přetečení, klikněte pravým tlačítkem myši na název projektu v Průzkumník řešení a potom klikněte na příkaz **vlastnosti**. Klikněte na **kompilovat**, klikněte na **Pokročilé možnosti kompilace**a potom zaškrtněte políčko **Odebrat kontroly přetečení celých čísel**.

<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->

## <a name="see-also"></a>Viz také
 <xref:System.IDisposable>[Vzor Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)