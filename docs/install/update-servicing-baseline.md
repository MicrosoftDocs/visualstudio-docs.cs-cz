---
title: Aktualizace sady Visual Studio v servisním směrném plánu
description: Naučte se aktualizovat Visual Studio a přitom zachováváte se směrným plánem údržby.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: '>=vs-2019'
ms.openlocfilehash: f185451a7f12c3c0b24d74d4a24b40d986ec536f
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184390"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aktualizace sady Visual Studio v servisním směrném plánu

Visual Studio aktualizujeme často během životního cyklu produktu. Existují dva typy aktualizací: 

* **Aktualizace** &mdash; podverze například 16,0 na 16,1 &mdash; , které obsahují nové funkce a součásti.  
* **Servisní aktualizace**– například 16.0.4 do 16.0.5 – to zahrnuje jenom cílené opravy pro kritické problémy.

Podnikoví správci si můžou zachovávat své klienty na standardních hodnotách údržby. Směrné plány údržby se podporují s aktualizacemi údržby po dobu v roce po vydání příštího směrného plánu údržby.

Možnost standardních hodnot obsluhy dává vývojářům a správcům větší flexibilitu, aby mohla přijímat nové funkce, opravy chyb nebo součásti, které jsou součástí nových menších aktualizací. První směrný plán obsluhy je 16.0. x. Další informace najdete v tématu [Možnosti podpory pro zákazníky v organizacích Enterprise a Professional](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Jak se dostat do směrného plánu údržby

Pokud chcete začít používat směrný plán údržby, Stáhněte si z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)zaváděcí nástroj pro instalaci sady Visual Studio s pevnou verzí. Zaváděcí nástroje mají odkazy na konfigurace produktů, úlohy a komponenty pro danou konkrétní verzi.

> [!NOTE]
> Buďte opatrní, abyste rozlišili zaváděcí nástroj pro pevné verze a standardní zavaděče. Standardní zaváděcí nástroje jsou nakonfigurovány k používání nejnovější dostupné verze sady Visual Studio. Standardní boostrappers má v názvu souboru číslo (například vs_enterprise__123456789 -123456789. exe), když se stáhnou z My.VisualStudio.com.

Během instalace musí správci organizace nakonfigurovat klienty tak, aby klientům zabránili v aktualizaci na nejnovější verzi. To lze provést několika způsoby:
- [Změňte `channelUri` nastavení v konfiguračním souboru odpovědi](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) tak, aby používalo manifest kanálu v rozložení nebo místní složce.
- [Upravte parametr channeluri prostřednictvím příkazového řádku](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) , aby se použil neexistující soubor.
- [Nastavením zásad v klientském systému zakážete aktualizace](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating)a zabráníte klientům v automatických aktualizacích.

### <a name="install-a-servicing-baseline-on-a-network"></a>Instalace směrného plánu údržby do sítě

Správci, kteří používají instalaci rozložení sítě, by měli upravit `channelUri` hodnotu v souboru *Response. JSON* v rozložení tak, aby používala soubor *channelmanifest. JSON* , který je ve stejné složce. Postup, jak provést, najdete v tématu [řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md). Změna `channelUri` hodnoty umožňuje klientům vyhledávat aktualizace v umístění rozložení.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Instalace standardních hodnot obsluhy prostřednictvím Internetu

Pro internetovou instalaci přidejte do `--channelUri` příkazového řádku, který se používá ke spuštění instalačního programu, neexistující manifest kanálu. Tím zakážete aplikaci Visual Studio v použití nejnovější dostupné verze aktualizace. Tady je příklad:

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Použití nastavení zásad k zakázání aktualizací klientů

Další možností kontroly aktualizací klienta je vypnutí [oznámení o aktualizacích](controlling-updates-to-visual-studio-deployments.md). Tuto možnost použijte, pokud se hodnota parametr channeluri při instalaci nezměnila. Zakáže klientovi příjem odkazů na nejnovější dostupnou verzi. Pro aktualizaci na konkrétní verzi klienta je nutné, aby byl nástroj pro spouštění s pevnou verzí stále nezbytný.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Jak zůstat v rámci standardních hodnot údržby

Pokud je k dispozici aktualizace pro standardní hodnoty údržby, jsou soubory zaváděcího nástroje opravené verze dostupné pro servisní aktualizaci na adrese [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0).

Pro správce, kteří nasazují pomocí instalace rozložení sítě, by měl správce aktualizovat [umístění rozložení](update-a-network-installation-of-visual-studio.md). Klienti, kteří jsou nainstalováni z umístění, budou dostávat oznámení o aktualizacích. Pokud se aktualizace musí nasadit na klienty, postupujte podle [těchto pokynů](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines). Když upravujete Response. JSON pro aktualizaci, nepřidáte další úlohy, součásti ani jazyky. Správa těchto nastavení se musí provádět jako nasazení úprav po aktualizaci produktu.

Pro internetovou instalaci spusťte nový zaváděcí nástroj pevné verze s `--channelUri` parametrem odkazujícím na neexistující manifest kanálu na klientovi. Pokud je aktualizace nasazená v tichém nebo pasivním režimu, použijte dva samostatné příkazy:

1. Aktualizace instalačního programu sady Visual Studio:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Aktualizace samotné aplikace sady Visual Studio:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Definování nastavení v souboru odpovědí](automated-installation-with-response-file.md)
* [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
