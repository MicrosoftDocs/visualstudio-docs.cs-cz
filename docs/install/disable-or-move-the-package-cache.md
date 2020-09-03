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
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f38757931cb22e9072571d96b015f37882dd500
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114788"
---
# <a name="disable-or-move-the-package-cache"></a>Zakázání nebo přesunutí mezipaměti balíčku

Mezipaměť balíčků poskytuje zdroj nainstalovaných balíčků pro případ, že budete potřebovat opravit sadu Visual Studio nebo jiné související produkty v případě, že nemáte připojení k Internetu. U některých jednotek nebo systémových nastavení je ale možné, že nebudete chtít, aby všechny tyto balíčky byly v okolí.
Instalační program je v případě potřeby stáhne, takže pokud chcete ušetřit nebo obnovovat místo na disku, můžete mezipaměť balíčku zakázat nebo přesunout.

## <a name="disable-the-package-cache"></a>Zakázat mezipaměť balíčku

Před instalací, úpravou nebo opravou sady Visual Studio nebo jiných produktů pomocí nového instalačního programu můžete spustit instalační program s `--nocache` přepínačem na instalační program.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Jakákoli operace s jakýmkoli produktem odebere všechny existující balíčky pro daný produkt a nebude ukládat žádné balíčky po instalaci. Pokud je nutné upravit nebo opravit Visual Studio a balíčky, budou automaticky staženy a odebrány po jejich instalaci.

Pokud chcete mezipaměť znovu povolit, předejte `--cache` místo toho. Do mezipaměti budou uloženy pouze balíčky, které jsou požadovány, takže pokud potřebujete obnovit všechny balíčky, měli byste před odpojením od sítě opravit aplikaci Visual Studio.

```cmd
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
