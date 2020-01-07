---
title: Zakázání nebo přesunutí mezipaměti balíčku
description: Zjistěte, jak zakázat, povolit nebo přesunutí mezipaměti balíčku pro nasazení sady Visual Studio.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 276eff442891f70b9eea76e9167b07f798af2d6a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591460"
---
# <a name="disable-or-move-the-package-cache"></a>Zakázání nebo přesunutí mezipaměti balíčku

Mezipaměť balíčků poskytuje zdroj balíčků nainstalovaných v případě, že potřebujete opravit Visual Studio nebo další související produkty v případech, kdy mají bez připojení k Internetu. U některých jednotek nebo systémových nastavení je ale možné, že nebudete chtít, aby všechny tyto balíčky byly v okolí.
Instalační program je v případě potřeby stáhne, takže pokud chcete ušetřit nebo obnovovat místo na disku, můžete mezipaměť balíčku zakázat nebo přesunout.

## <a name="disable-the-package-cache"></a>Zakázat mezipaměť balíčku

Před instalací, upravit nebo opravte Visual Studio nebo jiné produkty s novým instalačním programem, můžete spustit instalační program s `--nocache` přepnout do instalačního programu.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Všechny operace, které vám v žádném produktu odebere všechny existující balíčky pro tento produkt a vyhnete se ukládají všechny balíčky, které se po instalaci. Pokud upravíte nebo opravte Visual Studio a balíčky jsou požadovány, bude se automaticky se stáhne a odebrána po instalaci.

Pokud chcete znovu povolit mezipaměť, předejte `--cache` místo. Do mezipaměti budou uloženy pouze balíčky, které jsou požadovány, takže pokud potřebujete obnovit všechny balíčky, měli byste před odpojením od sítě opravit aplikaci Visual Studio.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Můžete také nastavit `KeepDownloadedPayloads` [zásad registru](set-defaults-for-enterprise-deployments.md) zakázání ukládání do mezipaměti, před instalací, upravit nebo opravte Visual Studio.

## <a name="move-the-package-cache"></a>Přesunutí mezipaměti balíčku

Běžnou konfigurací systému je mít pro vývoj pro Windows nainstalované na SSD s větší pevného disku (nebo více) potřebuje, jako je zdrojový kód, binární soubory aplikace a další. Pokud chcete pracovat offline, můžete místo toho přesunout mezipaměť balíčku.

V současné době to můžete provést pouze v případě, že jste nastavili [zásady registru](set-defaults-for-enterprise-deployments.md) `CachePath` před instalací, úpravou nebo opravou sady Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Výchozí nastavení v případě podnikového nasazení](set-defaults-for-enterprise-deployments.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
