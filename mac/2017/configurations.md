---
title: Principy konfigurací sestavení
description: Tento článek popisuje různé konfigurace sestavení v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 0bd35d415a60ea64c479b19cb506c58c2c346cc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74983592"
---
# <a name="understanding-build-configurations"></a>Principy konfigurací sestavení

## <a name="project-build-configurations"></a>Konfigurace sestavení projektu

Projekty mají více konfigurací a přepínání mezi nimi umožňuje různé výstupy v době sestavení. Například konfigurace ladění bude výstupem symbolů ladění, což umožňuje ladicímu programu překládat názvy, parametry a proměnné funkcí z chybných trasování zásobníku aplikace. I když jsou tyto další informace užitečné během vývoje, vede k neploché velikosti souborů a nejsou ideální pro distribuci.

Každá platforma má specifické konfigurace pro sestavení.

## <a name="solution-configurations"></a>Konfigurace řešení

Podobají konfigurace projektu – konfigurace řešení se používají k vytváření vlastních konfigurací pro celý projekt. Pomocí karty **mapování konfigurace** pod položkou **Konfigurace > sestavení** můžete přiřadit cílovou konfiguraci pro každou položku řešení, jak je znázorněno na následujícím obrázku:

![Možnosti mapování konfigurace](media/projects-and-solutions-image3.png)

Další informace o konfiguracích najdete v tématu [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) video od James Montemagno.

## <a name="run-configuration"></a>Konfigurace spuštění

V předchozích verzích Xamarin Studio můžete vybrat možnost pro nastavení projektu jako **spouštěný projekt**, což je projekt, který je spuštěn nebo laděn při použití globálního příkazu Spustit/ladit. To bylo označeno tučným písmem pro název projektu na panelu projektu.

V Visual Studio pro Mac místo nastavení spouštěného projektu můžete nastavit _konfiguraci spuštění_. Konfigurace spuštění jsou uvedeny v rozevíracím seznamu na panelu nástrojů vedle selektoru konfigurace sestavení, jak je znázorněno níže:

![Rozevírací seznam konfigurace spuštění](media/projects-and-solutions-image8.png)

Konfigurace spuštění je sada možností spuštění s názvem a několika konfiguracemi, které jsou definovány v projektu pro různé účely. Konfigurace spuštění jsou definovány na úrovni projektu a výchozí nastavení se vytvoří automaticky pro každý spustitelný projekt, i když je možné přidat tolik, kolik potřebujete. Některé typy projektů automaticky generují další konfigurace spuštění. Například projekty watchOS mohou generovat  _přehledy a konfigurace oznámení._

Konfigurace je možné sdílet s jinými vývojáři (v takovém případě se konfigurace uloží v souboru. csproj) nebo v místním počítači (v takovém případě budou uloženy v souboru. User).

### <a name="android-run-configurations"></a>Konfigurace spuštění Androidu

Konfigurace spuštění pro projekty pro Android vám umožní určit, která aktivita, služba nebo přijímač všesměrového vysílání se spustí při spuštění nebo ladění projektu. Můžete předat doplňující data a nastavit příznaky záměru, aby bylo možné testovat komponenty v rámci různých podmínek spuštění.

Jiné aktivity než musí `MainLauncher` být `Exported=true` přidány do atributu Activity pro ladění na fyzickém zařízení nebo mají definovány filtry záměrů.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Příklady dat, která mohou být součástí konfigurací spuštění

Následující seznam obsahuje příklady dat, která mohou být součástí konfigurací spuštění:

* Běžný projekt .NET
  * Alternativní úvodní aplikace
  * Počáteční argumenty
  * Pracovní adresář
  * Proměnné prostředí
  * Možnosti Mono runtime (budou použity pouze při spuštění na mono)
* Projekt pro Android
  * Vstupní bod (aktivita, služba, přijímač)
  * Argumenty záměru a data
* projekt iOS
  * Režim (normální, načítání na pozadí)
* projekt rozšíření pro iOS
  * Aplikace po spuštění: výchozí nebo vlastní
* Projekt WatchKit
  * Režim (stručný přehled, oznámení)
  * Datová část oznámení

## <a name="see-also"></a>Viz také

- [Principy konfigurací sestavení (Visual Studio ve Windows)](/visualstudio/ide/understanding-build-configurations)
