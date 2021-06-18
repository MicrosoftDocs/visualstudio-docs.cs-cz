---
title: Zakázání nebo přesunutí mezipaměti balíčku
description: Přečtěte si, jak zakázat, povolit nebo přesunout mezipaměť balíčků pro nasazení sady Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0584673880a56bbde0ef44ad14c24acca252c5a2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307476"
---
# <a name="disable-or-move-the-package-cache"></a>Zakázání nebo přesunutí mezipaměti balíčku

Mezipaměť balíčků poskytuje zdroj nainstalovaných balíčků pro případ, že budete potřebovat opravit sadu Visual Studio nebo jiné související produkty v případě, že nemáte připojení k Internetu. U některých jednotek nebo systémových nastavení je ale možné, že nebudete chtít, aby všechny tyto balíčky byly v okolí.
Instalační program je v případě potřeby stáhne, takže pokud chcete ušetřit nebo obnovovat místo na disku, můžete mezipaměť balíčku zakázat nebo přesunout.

## <a name="disable-the-package-cache"></a>Zakázat mezipaměť balíčku

Před instalací, úpravou nebo opravou sady Visual Studio nebo jiných produktů pomocí nového instalačního programu můžete spustit instalační program s `--nocache` přepínačem na instalační program.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Jakákoli operace s jakýmkoli produktem odebere všechny existující balíčky pro daný produkt a nebude ukládat žádné balíčky po instalaci. Pokud je nutné upravit nebo opravit Visual Studio a balíčky, budou automaticky staženy a odebrány po jejich instalaci.

Pokud chcete mezipaměť znovu povolit, předejte `--cache` místo toho. Do mezipaměti budou uloženy pouze balíčky, které jsou požadovány, takže pokud potřebujete obnovit všechny balíčky, měli byste před odpojením od sítě opravit aplikaci Visual Studio.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Můžete také nastavit `KeepDownloadedPayloads` [zásady registru](set-defaults-for-enterprise-deployments.md) , které zakazují mezipaměť před instalací, úpravou nebo opravou sady Visual Studio.

## <a name="move-the-package-cache"></a>Přesunout mezipaměť balíčku

Běžnou konfigurací systému je instalace Windows na disk SSD s větším pevným diskem (nebo více) pro potřeby vývoje, jako je zdrojový kód, binární soubory programu a další. Pokud chcete pracovat offline, můžete místo toho přesunout mezipaměť balíčku.

V současné době to můžete provést pouze v případě, že jste nastavili `CachePath` [zásady registru](set-defaults-for-enterprise-deployments.md) před instalací, úpravou nebo opravou sady Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Nastavení výchozích hodnot pro podniková nasazení](set-defaults-for-enterprise-deployments.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
