---
title: 'Základní informace o ladění: Okno registrů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27337c5bea0d0216b27411dc5e91d7ca4c778615
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722330"
---
# <a name="debugging-basics-registers-window"></a>Základní informace k ladění: okno registrů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Zaregistruje** není k dispozici pouze v případě, že je povoleno ladění úrovni adres v interval **možnosti** dialogovém okně **ladění** uzlu.  
  
 Registry jsou speciální umístění v rámci procesoru (CPU), které se používají k ukládání dat, která procesor aktivně pracuje na malé části. Kompilace a interpretace zdrojový kód generuje pokyny, které přesouvají data z paměti do registrů a zpět, podle potřeby. Přístup k datům v registrech, je velmi rychlé zpracování ve srovnání s přístup k datům v paměti, takže kód, který umožňuje procesor zachovat data v registru a opakovaně k němu přístup se obvykle provádějí rychleji než kód, který vyžaduje procesor, který se neustále načtení a uvolnění registrů. Aby bylo snazší pro kompilátor zachovat data v registrech a provádět další optimalizace, by měl neměli používat globální proměnné a závisí na místních proměnných co nejvíc. Kód napsaný tímto způsobem se říká, že máte dobré místo odkazu. V některých jazycích, jako je C/C++ programátor můžete deklarovat proměnnou registru, který instruuje kompilátor, aby zkuste nejlépe, mějte na proměnné registru za všech okolností. Další informace najdete v tématu [zaregistrovat – klíčové slovo](http://msdn.microsoft.com/en-us/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 Registry je možné rozdělit do dvou typů: obecné účely a zvláštní účely. Pro obecné účely registrů uchovávání dat pro obecné operace, jako jsou sečtení dvou čísel nebo odkazující na prvek v poli. Speciální registry mají zvláštní účely a zvláštní význam. Dobrým příkladem je ukazatel zásobníku registru, který procesor používá ke sledování zásobníku volání. Jako programátor bude ukazatel zásobníku manipulovat pravděpodobně není přímo. Je však nezbytné pro správné fungování programu, protože procesor nemusí bez ukazatel zásobníku věděli, kde se vraťte na konci volání funkce.  
  
 Většina pro obecné účely registrů obsahovat pouze jeden datový prvek. Například celá čísla, čísla s plovoucí desetinnou čárkou nebo prvek pole. Některé novější procesory mají větší registrů, volá vektorové registry, které může obsahovat malé pole dat. Protože drží množství dat, povolit vektorové registry operace, které zahrnují pole, která se má provést velmi rychle. Vektorové registry na nákladné a vysoce výkonnou superpočítače nejprve používaly ale se stávají nyní k dispozici na mikroprocesory, kde se používá pro skvělé výhody v grafické operace náročné na prostředky.  
  
 Procesor obvykle má dvě sady pro obecné účely registrů, jeden optimalizované pro operace s plovoucí desetinnou čárkou a druhou pro celočíselné operace. Logicky se označují jako s plovoucí desetinnou čárkou a celočíselné registry.  
  
 Spravovaný kód je zkompilován za běhu a nativní kód, který má přístup k fyzické registrech procesoru. **Zaregistruje** v okně se zobrazí tyto fyzické registrů pro modul common language runtime nebo nativní kód. **Zaregistruje** okno nezobrazí informace registru pro skript nebo aplikaci SQL, protože skript a SQL jsou jazyky, které nepodporují koncept registrů.  
  
 Další informace o zobrazení **zaregistruje** okna, naleznete v tématu [použití okna Registry](../debugger/how-to-use-the-registers-window.md).  
  
 Když se podíváte na **zaregistruje** okně se zobrazí položky jako je například v tomto příkladu:  
  
```  
EAX = 003110D8  
```  
  
 V tomto případě je název registru EAX, symbol nalevo od znak =. Číslo vpravo od znak = představuje obsah registru.  
  
 **Zaregistruje** okno umožňuje provádět více než jen zobrazení obsahu registru. Když jste v režimu pozastavení v nativním kódu, můžete kliknout na obsah registru a upravit její hodnotu. To je něco, co byste měli dělat náhodně. Pokud nerozumíte do registru, který upravujete a data, která obsahuje výsledek nepozorný úpravy by mohla být selhání program nebo jiné nežádoucí důsledky. Bohužel podrobné vysvětlení registr sady různých procesorů Intel a kompatibilní s verzí Intel dalece přesahuje rozsah Tento stručný úvod.  
  
## <a name="register-groups"></a>Registrovat skupiny  
 Pro přehlednost, **zaregistruje** okno uspořádá registry do skupiny. Pokud kliknete pravým tlačítkem **zaregistruje** okně se zobrazí místní nabídku, který obsahuje seznam skupin, které můžete zobrazit nebo skrýt podle svých potřeb.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití okna registry](../debugger/how-to-use-the-registers-window.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)





