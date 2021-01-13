---
title: Nepovedlo se nastavit zarážku dat | Microsoft Docs
description: Vyhledejte vysvětlení, řešení a alternativní řešení pro "nelze nastavit chyby zarážek dat", ke kterým dochází při změně hodnoty při použití možnosti "přerušit změny".
ms.custom: SEO-VS-2020
ms.date: 12/3/2019
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
ms.openlocfilehash: 4e90c3d4af8e568f1bb2e6987c66c7fbc0856c57
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150454"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Řešení chyb zarážek dat
Tato stránka vás provede při řešení běžných chyb, ke kterým dochází při použití možnosti "přerušit při změně hodnoty".

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnostikování chyb "nelze nastavit datovou zarážku"
> [!IMPORTANT]
> Spravované datové zarážky jsou podporovány v rozhraní .NET Core 3,0 a up. Nejnovější verzi si můžete stáhnout [tady](https://dotnet.microsoft.com/download).

Níže je uveden seznam chyb, ke kterým může dojít při použití spravovaných datových zarážek. Obsahují další vysvětlení, proč došlo k chybě, a možná řešení nebo alternativní řešení chyby řešení.

- *"Verze rozhraní .NET používaná cílovým procesem nepodporuje datové zarážky. Datové zarážky vyžadují .NET Core 3.0 + běžící na platformě x86 nebo x64.*

  - Podpora spravovaných datových zarážek začala v .NET Core 3,0. V současné době není podporována v .NET Framework nebo ve verzi rozhraní .NET Core v 3,0. 
    
  - **Řešení**: k tomuto řešení by bylo možné upgradovat projekt na .net Core 3,0.

- *Hodnota se nedá najít na spravované haldě a nedá se sledovat.*
  - Proměnná je deklarována v zásobníku.
    - Nepodporujeme nastavení zarážek dat pro proměnné vytvořené v zásobníku, protože tato proměnná bude po ukončení funkce neplatná.
    - **Alternativní řešení**: Nastavte zarážky na řádcích, kde je proměnná používána.

  - "Přerušit při změně hodnoty" na proměnnou, která není rozbalena z rozevíracího seznamu.
    - Ladicí program interně potřebuje znát objekt obsahující pole, které chcete sledovat. Systém uvolňování paměti může přesunout objekt kolem haldy, aby ladicí program musel znát objekt, který má proměnnou, kterou chcete sledovat. 
    - **Alternativní řešení**: Pokud jste v rámci objektu, na kterém chcete nastavit zarážku dat, můžete přejít o jeden snímek nahoru a použít `locals/autos/watch` okno k rozšíření objektu a nastavení datové zarážky pro pole, které chcete.

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

## <a name="data-breakpoint-hardware-limitations"></a>Omezení hardwaru datových zarážek

Architektura (konfigurace platformy), na které se program spouští, má omezený počet zarážek hardwarových dat, které může použít. Následující tabulka uvádí, kolik registrů je k dispozici pro použití v rámci architektury.

| Architektura | Počet datových zarážek podporovaných hardwarem | Maximální velikost v bajtech|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Poskytnutí zpětné vazby

Pokud máte nějaké problémy nebo návrhy této funkce, dejte nám prosím vědět prostřednictvím Help > odeslání názoru > [nahlášení problému](../ide/how-to-report-a-problem-with-visual-studio.md) v integrovaném vývojovém prostředí nebo [komunitě vývojářů](https://aka.ms/feedback/suggest?space=8).

## <a name="see-also"></a>Viz také

- [Použití možnosti "přerušit při změně hodnoty" v .NET Core 3,0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [DevBlog: break při změně hodnoty: datové zarážky pro .NET Core v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
