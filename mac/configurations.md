---
title: Principy konfigurací sestavení
description: Tento článek popisuje různé konfigurace sestavení v sadě Visual Studio pro Mac
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 7f130f5dec77e0a1965c68cf71e642fdb636832f
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296174"
---
# <a name="understanding-build-configurations"></a>Principy konfigurací sestavení

## <a name="project-build-configurations"></a>Konfigurace sestavení projektu

Projekty obvykle obsahují více konfigurací a přepínání mezi nimi umožňuje různé výstupy v okamžiku sestavení. Konfigurace ladění bude například výstupu symboly pro ladění, což ladicímu programu přeložit názvy funkcí, parametry nebo proměnné z trasování zásobníku chyb aplikace. Zatímco tyto další informace jsou užitečné při vývoji, vede velikost zvýšeným souboru a není ideální pro distribuci.

Každá platforma má konkrétní konfigurací pro jeho sestavení.

## <a name="solution-configurations"></a>Konfigurace řešení

Podobají konfigurace projektu se konfigurace řešení používají k vytvoření vlastní konfigurace pro celý projekt. S použitím **mapování konfigurace** kartu **sestavení > Konfigurace** položky, můžete přiřadit cílovou konfiguraci pro každou položku řešení, jak je znázorněno v na následujícím obrázku:

![Možnosti konfigurace mapování](media/projects-and-solutions-image3.png)

Další informace o konfiguracích najdete v článku [nástroje Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) video od Jamese Montemagno.

## <a name="run-configuration"></a>Konfigurace spuštění

V předchozích verzích nástroje Xamarin Studio, můžete vybrat možnost nastavit jako projekt **spouštěný projekt**, což je projekt, který je spustit/ladit při použití příkazu globální spuštění/ladění. To byl označen tučné písmo pro název projektu v oblasti projektu.

V sadě Visual Studio pro Mac, namísto nastavení spouštěný projekt, můžete nastavit _konfigurace spuštění_. Spuštění konfigurace jsou uvedeny v rozevíracím seznamu na panelu nástrojů vedle selektor konfigurace sestavení, jak je znázorněno níže:

![Spustit rozevíracího seznamu konfigurace](media/projects-and-solutions-image8.png)

Konfigurace spuštění je sada možností spuštění s názvem a některé konfigurace, které jsou definovány v projektu pro různé účely. Spuštění konfigurace jsou definovány na úrovni projektu a výchozí vytvoří automaticky pro každý spustitelný projekt, i když je možné přidat, kolik potřebné. Některé typy projektu automaticky generovat další konfigurace spuštění. Například na projekty watchOS mohou generovat  _konfigurace přehledu a oznámení._

Konfigurace můžete sdílet s ostatními vývojáři (v takovém případě bude se vaše konfigurace bude uložen v souboru .csproj) nebo uložený místně (v takovém případě budou uloženy v souboru .user).

### <a name="android-run-configurations"></a>Android konfigurace spuštění

Spuštění konfigurace pro projekty pro Android umožňují určit, kterou aktivitu, službu nebo přijímač všesměrového vysílání spustit při spuštění nebo ladění projektu. Můžete předat záměru doplňující data a Nastavení záměru příznaků, které mít možnost Testovat vaše komponenty v rámci podmínek pro jiný spuštění.

Aktivity jinak než `MainLauncher` bude muset mít `Exported=true` přidána do aktivity atribut pro ladění na fyzickém zařízení, nebo jste definovali záměru filtry.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Mezi data, která může být součástí konfigurace spuštění

Následující seznam obsahuje několik příkladů dat, která může být součástí konfigurace spuštění:

* Pravidelné projektové .NET
    * Alternativní umístění pro spouštění aplikací
    * Počáteční argumenty
    * Pracovní adresář
    * Proměnné prostředí
    * Modul mono runtime možnosti (který se má použít jenom při spouštění v Mono)
* Projekt pro Android
    * Vstupní bod (aktivity, služby, příjemce)
    * Záměru argumenty a data
* projekt pro iOS
    * Režim (normální, načítání na pozadí)
* projekt rozšíření pro iOS
    * Při spuštění aplikace: výchozí nebo vlastní
* Projekt WatchKit
    * Režim (první pohled, oznámení)
    * Datová část oznámení

## <a name="see-also"></a>Viz také:

- [Principy konfigurací sestavení (Visual Studio na Windows)](/visualstudio/ide/understanding-build-configurations)