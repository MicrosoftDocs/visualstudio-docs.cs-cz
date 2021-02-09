---
title: Nastavení vlastního umístění souboru protokolu (chyby nasazení ClickOnce)
description: Seznamte se se soubory aktivačních protokolů, které ClickOnce udržuje pro všechna nasazení, které dokumentují chyby pro instalaci a inicializaci nasazení ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e527e1aec630faadec6e594f944a6715028c6d82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885050"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Postupy: nastavení vlastního umístění souboru protokolu pro chyby nasazení ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] udržuje soubory protokolu aktivace pro všechna nasazení. Tyto protokoly dokumentují všechny chyby, které se týkají instalace a inicializace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vytvoří jeden soubor protokolu pro každou aktivaci nasazení. Tyto soubory protokolu se uloží do složky dočasných internetových souborů. Soubor protokolu pro nasazení se uživateli zobrazí, když dojde k selhání aktivace a uživatel klikne na **Podrobnosti** v dialogovém okně výsledné chyby.

 Toto chování můžete změnit pro konkrétního klienta pomocí Editoru registru (**regedit.exe**) a nastavit tak vlastní cestu k souboru protokolu. V takovém případě [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] protokoluje úspěšné a neúspěšné aktivace pro všechna nasazení v jednom souboru.

> [!CAUTION]
> Pokud používáte Editor registru nesprávně, může dojít k vážným problémům, které mohou vyžadovat přeinstalaci operačního systému. Editor registru použijte na vlastní riziko.

> [!NOTE]
> Soubor protokolu bude někdy potřeba zkrátit nebo odstranit, aby se zabránilo jeho většímu růstu.

 Následující postup popisuje, jak nastavit vlastní umístění souboru protokolu pro jednoho klienta.

### <a name="to-set-a-custom-log-file-location"></a>Nastavení vlastního umístění souboru protokolu

1. Otevřete **Regedit.exe**.

2. Přejděte k uzlu `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Nastavte hodnotu řetězce `LogFilePath` na úplnou cestu a název souboru upřednostňovaného vlastního umístění protokolu.

     Toto umístění musí být v adresáři, ke kterému má uživatel oprávnění k zápisu. Například v systému Windows Vista vytvořte následující strukturu složek a nastavte `LogFilePath` ji na *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Viz také
- [Řešení potíží s nasazeními ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)