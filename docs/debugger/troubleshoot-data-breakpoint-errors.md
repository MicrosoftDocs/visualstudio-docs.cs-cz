---
title: Nelze nastavit zarážku dat | Microsoft Docs
description: Vyhledejte vysvětlení, řešení a alternativní řešení pro chybu "Nelze nastavit chyby datových zarážek", ke kterým dochází při použití funkce Break when Value Changes (Přerušení při změně hodnoty).
ms.custom: SEO-VS-2020
ms.date: 5/19/2020
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 73e7e02d90e2a89c81b5e690718c95fe7efe0fb3
ms.sourcegitcommit: 6e27b1238a8aa704b127eac34f4173e9d56690c5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2021
ms.locfileid: "110231962"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Řešení potíží s chybami datových zarážek
Tato stránka vás provede řešením běžných chyb, ke které dochází při použití funkce Break when Value Changes (Přerušit při změně hodnoty).

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnostika chyb "Nelze nastavit zarážku dat"
> [!IMPORTANT]
> Spravované datové zarážky se podporují v .NET Core 3.0 a více a .NET 5.0.3 a více. Nejnovější verzi si můžete stáhnout [tady:](https://dotnet.microsoft.com/download).

Níže je seznam chyb, ke kterým může dojít při použití spravovaných datových zarážek. Obsahují další vysvětlení, proč k chybě dochází, a možná řešení nebo alternativní řešení, jak chybu vyřešit.

- *"Verze rozhraní .NET používaná cílovým procesem nepodporuje datové zarážky. Datové zarážky vyžadují .NET Core 3.x nebo .NET 5.0.3+, běžící na x86 nebo x64.*

  - Podpora spravovaných datových zarážek byla zahájena v .NET Core 3.0. V současné době se nepodporuje v .NET Framework, verzích .NET Core ve verzi 3.0 ani ve verzích .NET ve verzi 5.0.3. 
    
  - **Řešení:** Řešením je upgradovat projekt na .NET Core 3.0.

- *Hodnotu nelze najít ve spravované haldě a nelze ji sledovat.*
  - Proměnná deklarovaná v zásobníku.
    - Nastavení datových zarážek pro proměnné vytvořené v zásobníku nepodporujeme, protože tato proměnná bude po ukončení funkce neplatná.
    - **Alternativní** řešení: Nastavte zarážky na řádcích, kde se proměnná používá.

  - Na proměnné, která není rozbalená z rozevíracího seznamu, se zobrazí "Break when Value changes" (Přerušit při změně hodnoty).
    - Ladicí program potřebuje interně znát objekt obsahující pole, které chcete sledovat. Systém uvolňování paměti může přesouvat objekt v haldě, takže ladicí program bude potřebovat znát objekt, který obsahuje proměnnou, kterou chcete sledovat. 
    - **Alternativní** řešení: Pokud jste v metodě v rámci objektu, u kterého chcete nastavit datovou zarážku, přejděte o jeden snímek nahoru a pomocí okna rozbalte objekt a nastavte datovou zarážku na `locals/autos/watch` pole, které chcete.

- *"Datové zarážky nejsou podporovány u statických polí nebo statických vlastností."*
    
  - Statická pole a vlastnosti se v tuto chvíli nepodporují. Pokud vás zajímá Tato funkce, poskytněte nám prosím [svůj názor](#provide-feedback).

- *"Pole a vlastnosti struktur nelze sledovat".*

  - Pole a vlastnosti struktur nejsou aktuálně podporovány. Pokud vás zajímá Tato funkce, poskytněte nám prosím [svůj názor](#provide-feedback).

- *"Hodnota vlastnosti se změnila a nelze ji již sledovat."*

  - Vlastnost může změnit způsob výpočtu během běhu a v případě, že k tomu dojde, počet proměnných, jejichž vlastnost závisí na zvýšení a může překročit omezení hardwaru. Viz `"The property is dependent on more memory than can be tracked by the hardware."` níže.

- *"Vlastnost je závislá na více paměti, než je možné sledovat hardwarem."*
    
  - Každá architektura má nastaven počet bajtů a zarážky hardwarových dat, které může podporovat, a vlastnost, u které chcete nastavit zarážku dat, překročila tento limit. Informace o tom, kolik datových zarážek a bajtů podporovaných hardwarem pro architekturu, kterou používáte, najdete v tabulce [omezení hardwaru datových zarážek](#data-breakpoint-hardware-limitations) . 
  - **Alternativní řešení**: Nastavte zarážku dat na hodnotu, která se může změnit v rámci vlastnosti.

- *"Při použití starší verze vyhodnocovacího filtru výrazů jazyka C# nejsou podporovány datové zarážky."*

  - Datové zarážky jsou podporovány pouze v vyhodnocovacím filtru výrazů v jazyce C#, který není starší verze. 
  - **Řešení**: starší verze filtru výrazů C# zakážete tak, že `Debug -> Options` v části zrušíte `Debugging -> General` kontrolu `"Use the legacy C# and VB expression evaluators"` .

- *"Class **X** má vlastní zobrazení ladicího programu, které blokuje použití datových zarážek pro data specifická pouze pro IT."*
  
  - Datové zarážky jsou podporovány pouze v paměti, která je vytvořena cílovým procesem (aplikace, která je právě laděna). Paměť, na které je nastavovaná datová zarážka, byla označena příznakem tak, aby mohla být vlastněna objektem vytvořeným [atributem používání DebuggerTypeProxy](using-debuggertypeproxy-attribute.md) nebo něčím jiným, který není součástí cílového procesu.
  - **Alternativní** řešení: Místo rozbalení zobrazení DebuggerTypeProxy objektů rozbalte nezpracované zobrazení objektů a pak nastavte datovou zarážku. To zaručuje, že datová zarážka není v paměti vlastněná objektem vytvořeným atributem DebuggerTypeProxy.

## <a name="data-breakpoint-hardware-limitations"></a>Hardwarová omezení datových zarážek

Architektura (konfigurace platformy), na které program běží, má omezený počet hardwarových datových zarážek, které může používat. Následující tabulka uvádí, kolik registrů je možné použít pro každou architekturu.

| Architektura | Počet hardwarově podporovaných datových zarážek | Maximální velikost byte|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Poskytnutí zpětné vazby

Pokud máte jakékoli problémy nebo návrhy týkající se této funkce, dejte nám vědět prostřednictvím nápovědy > Poslat názor > [Nahlásit](../ide/how-to-report-a-problem-with-visual-studio.md) problém v integrovaném vývojovém prostředí nebo v [Developer Community](https://aka.ms/feedback/suggest?space=8).

## <a name="see-also"></a>Viz také

- Použití funkce Break when Value changes v [.NET Core 3.0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)
- [DevBlog: Break When Value Changes: Datové zarážky pro .NET Core v Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
