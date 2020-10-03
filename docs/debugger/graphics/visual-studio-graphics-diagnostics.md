---
title: Diagnostika grafiky | Microsoft Docs
description: Úvod do sady Visual Studio Diagnostika grafiky.
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 829c51c0e2020a154dc485dbfc4db25e0b399e57
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671376"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio
>[!NOTE]
> Sada Visual Studio doporučuje PIX ve Windows pro hry DirectX 12. [Pix v systému Windows](https://aka.ms/PIXonWindows) je nástroj pro ladění a ladění výkonu, který plně podporuje rozhraní DirectX 12. [Přečtěte si další informace](visual-studio-graphics-diagnostics-directx-12.md) nebo [si ji stáhněte tady](https://aka.ms/downloadPIX).

Visual Studio *Diagnostika grafiky* je sada nástrojů pro zaznamenávání a analýzu problémů s výkonem a výkonem v aplikacích Direct3D. Diagnostika grafiky můžete použít pro aplikace, které běží místně na počítači s Windows, v emulátoru zařízení s Windows nebo na vzdáleném počítači nebo zařízení.

 Pracovní postup Diagnostika grafiky začíná zachycením záznamu o tom, jak vaše aplikace využívá Direct3D – Live, když je spuštěná, aby se jeho chování mohlo analyzovat hned, sdílet nebo Uložit pro pozdější použití. Relace zachycení lze spustit a řídit ručně ze sady Visual Studio nebo pomocí nástroje pro zachycení příkazového řádku **dxcap.exe**. Relace zachycení se taky dají iniciovat a řídit programově pomocí rozhraní API pro zachycení Diagnostika grafiky.

 Po nahrání jeho obsahu je možné ho pomocí *analyzátoru grafiky* sady Visual Studio kdykoli přehrát a znovu vytvořit zachycené snímky pomocí stejných prostředků a příkazů pro vykreslování, které aplikace používala. Pak můžete pomocí nástrojů, které jsou k dispozici v okně analyzátor grafiky, analyzovat všechny zachycené snímky podrobněji. Tyto nástroje je možné použít k prohlédnutí všech volání rozhraní Direct3D API, prostředku, objektu stavu kanálu, fáze zřetězení nebo dokonce kompletní historie libovolného pixelu v zachyceném snímku. Pomocí těchto nástrojů ve vzájemném seznámení se dá problém vykreslování zobrazit intuitivním způsobem, počínaje tím, jak se zobrazuje v zachyceném snímku a přechodem na jeho hlavní příčinu ve zdrojovém kódu aplikace, shaderech nebo grafických prostředcích.

 Chcete-li diagnostikovat problémy s výkonem, lze zachycený snímek analyzovat pomocí nástroje pro *analýzu snímků* . Tento nástroj zkoumá možné optimalizace výkonu tím, že automaticky změní způsob, jakým aplikace využívá Direct3D, a provádí srovnávací testy pro všechny variace. V minulosti jste mohli tyto druhy změn provést a podle srovnávacích testů přesně zjistit, které z nich byly rozdílové. S analýzou snímků je potřeba udělat jenom změny, které už znáte, a teprve potom budete platit.

 Diagnostika grafiky pomáhá grafickému a bohatě formátované aplikaci Direct3D vypadat a nejlépe ji spustit.

 Další informace o tom, co Visual Studio Diagnostika grafiky nabízí, najdete dál v [přehledu](overview-of-visual-studio-graphics-diagnostics.md) .

## <a name="in-this-section"></a>V tomto oddílu
 [Přehled](overview-of-visual-studio-graphics-diagnostics.md) Zavádí Diagnostika grafiky pracovní postup a nástroje.

 [Začínáme](getting-started-with-visual-studio-graphics-diagnostics.md) V této části se dozvíte, jak nainstalovat Visual Studio Diagnostika grafiky a jak začít používat Diagnostika grafiky s aplikací Direct3D.

 [Zachytávání informací grafiky](capturing-graphics-information.md) Pokud chcete použít Diagnostika grafiky k prohlédnutí problému s vykreslováním aplikace, nejprve si zaznamenejte informace o tom, jak aplikace používá rozhraní DirectX. Během relace nahrávání se při normálním spuštění aplikace *zachytí* (to znamená výběr) rámců, které vás zajímají. Zachycení obsahují podrobné informace o způsobu vykreslování rámců. Zachycené informace můžete uložit jako dokument protokolu grafiky pro pozdější prošetření nebo sdílení s ostatními členy týmu.

 [Využití GPU](../../profiling/gpu-usage.md) Pokud chcete použít Diagnostika grafiky k profilaci vaší aplikace, použijte nástroj využití GPU. Využití GPU se dá použít ve vzájemné součinnosti s jinými nástroji pro profilaci, jako je využití CPU, ke sladění aktivity CPU a GPU, které můžou přispět k problémům s výkonem ve vaší aplikaci.

 [Dokument protokolu grafiky](graphics-log-document.md) Chcete-li spustit kontrolu zaznamenaného protokolu grafiky, použijte okno dokument protokolu grafiky k výběru zachyceného snímku nebo dokonce konkrétního pixelu, aby bylo možné podrobněji prostudovat *události* (tj. volání rozhraní API DirectX), která to ovlivňují.

 [Analýza snímků](graphics-frame-analysis.md) Po výběru rámce použijete Analýza grafických snímků k prohlédnutí a optimalizaci výkonu vykreslování.

 [Seznam událostí](graphics-event-list.md) Po výběru rámce použijete **seznam událostí grafiky** k prohlédnutí jeho událostí, abyste zjistili, zda souvisejí s problémem vykreslování.

 [Stav](graphics-state.md) Okno stav vám pomůže pochopit stav grafiky, který je aktivní v době aktuální události.

 [Fáze zřetězení](graphics-pipeline-stages.md) V okně **fáze zřetězení grafiky** můžete prozkoumat, jak je aktuálně vybraná událost zpracována každou fází grafického kanálu, abyste mohli zjistit, kde se problém s vykreslováním zobrazuje poprvé. Prozkoumání fází zřetězení je obzvlášť užitečné, když se objekt neobjeví kvůli nesprávné transformaci, nebo když jedna z fází vytvoří výstup, který neodpovídá tomu, co další fáze očekává.

 [Zásobník volání událostí](graphics-event-call-stack.md) **Zásobník volání událostí grafiky** slouží k prohlédnutí zásobníku volání aktuálně vybrané události, abyste mohli přejít ke kódu aplikace, který se vztahuje k problému vykreslování.

 [Historie pixelů](graphics-pixel-history.md) Pomocí okna **Historie pixelů grafiky** můžete analyzovat, jak je aktuálně vybraný pixel ovlivněn událostmi, které ho ovlivnily, a můžete určit událost nebo kombinaci událostí, které způsobují určitý druh problémů s vykreslováním. Historie pixelů je užitečná hlavně v případě, že se objekt nesprávně vykresluje, protože výstup pixel shaderu je buď nesprávný, nebo byl nesprávně spojen s vyrovnávací pamětí snímku, nebo když se objekt dokonce nezobrazuje, protože jeho pixely byly zahozeny předtím, než dosáhnou vyrovnávací paměti rámce.

 [Tabulka objektů](graphics-object-table.md) **Tabulka grafických objektů** slouží k prohlédnutí vlastností a obsahu konkrétních objektů a prostředků Direct3D, které jsou platné pro aktuálně vybranou událost. Tabulka objektů vám může přispět k určení kontextu grafického zařízení, který je aktivní během události, a prozkoumávat obsah grafických prostředků, jako jsou konstanty vyrovnávací paměti, vyrovnávací paměti vrcholů a textury.

 [Ladicí program HLSL](hlsl-shader-debugger.md) Chcete-li se podívat, jak se kód shaderu pro aktuálně vybranou událost a vrstvu grafických kanálů chová, použijte **ladicí program HLSL** pro procházení kódu, Projděte si obsah proměnných a proveďte jiné typické úlohy ladění. Pomocí ladicího programu HLSL můžete také kontrolovat kód výpočetního shaderu bez ohledu na to, zda jsou výsledky dále zpracovávány grafickým kanálem nebo pouze zpětně čteny vaší aplikací.

 [Nástroj příkazového řádku pro zachycení](command-line-capture-tool.md) Použijte nástroj příkazového řádku pro zachycení k rychlému zachycení a přehrání grafické informace bez použití sady Visual Studio nebo programového zachycení. Konkrétně můžete použít nástroj pro zachycení z příkazového řádku pro automatizaci nebo v testovacím prostředí.

 [Příklady](graphics-diagnostics-examples.md) Několik příkladů ukazuje, jak používat Diagnostika grafiky nástroje společně ke diagnostikování různých druhů problémů s vykreslováním.

## <a name="related-sections"></a>Související oddíly

| Nadpis | Popis |
| - | - |
| [Prohlídka funkcí ladicího programu](../debugger-feature-tour.md) | Zavádí funkce ladění v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| [Grafika rozhraní DirectX a hry](/windows/win32/directx) | Poskytuje články, které popisují technologii DirectX Graphics Technologies. |
| [Podpora rozhraní DirectX 12 v aplikaci Visual Studio](visual-studio-graphics-diagnostics-directx-12.md) | Další informace o podpoře rozhraní DirectX 12 v aplikaci Visual Studio |
