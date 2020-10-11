---
title: Přepsání v nápovědě pro Content Manager
description: Přečtěte si o potlačení nápovědy Content Manageru, které mění výchozí chování aplikace Help Viewer a funkcí souvisejících s nápovědy v integrovaném vývojovém prostředí sady Visual Studio.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60f4e46d8c43c90759c964dbf01145d876a9f413
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91879057"
---
# <a name="help-content-manager-overrides"></a>Přepsání v nápovědě pro Content Manager

V integrovaném vývojovém prostředí sady Visual Studio můžete změnit výchozí chování aplikace Help Viewer a funkcí týkajících se nápovědy. Některé možnosti jsou určeny vytvořením souboru [. pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/) pro nastavení různých hodnot klíčů registru. Ostatní jsou nastaveny přímo v registru.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Jak ovládat chování aplikace Help Viewer pomocí souboru. pkgdef

1. Vytvořte soubor *. pkgdef* s prvním řádkem jako `[$RootKey$\Help]` .

2. Přidejte všechny nebo všechny hodnoty klíčů registru popsané v následující tabulce na samostatné řádky, například `"UseOnlineHelp"=dword:00000001` .

3. Zkopírujte soubor do *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\<Edition \> \Common7\IDE\CommonExtensions*.

4. Spustí se `devenv /updateconfiguration` na příkazovém řádku pro vývojáře.

### <a name="registry-key-values"></a>Hodnoty klíčů registru

|Hodnota klíče registru|Typ|Data|Description|
|------------------|----|----|-----------|
|NewContentAndUpdateService|řetězec|\<http URL for service endpoint\>|Definování jedinečného koncového bodu služby|
|UseOnlineHelp|hodnoty|`0` zadání místní nápovědě, pokud `1` chcete zadat online podporu|Definovat výchozí nastavení online nebo offline|
|OnlineBaseUrl|řetězec|\<http URL for service endpoint\>|Definování jedinečného koncového bodu F1|
|OnlineHelpPreferenceDisabled|hodnoty|`0` povolení nebo `1` Zakázání možnosti předvolby online pomocníka|Zakázat možnost předvoleb online nápovědě|
|DisableManageContent|hodnoty|`0` povolení nebo `1` zakázání karty **Spravovat obsah** v prohlížeči nápovědy|Zakázat kartu **Spravovat obsah**|
|DisableFirstRunHelpSelection|hodnoty|`0` Chcete-li povolit nebo `1` Zakázat funkce aplikace Help, které jsou konfigurovány při prvním spuštění sady Visual Studio|Zakázat instalaci obsahu při prvním spuštění sady Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Příklad obsahu souboru. pkgdef

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Změna chování prohlížeče nápovědy pomocí Editoru registru

Následující dvě chování lze ovládat nastavením hodnot klíčů registru v editoru registru.

|Úloha|Klíč registru|Hodnota|Data|
|----------|-----|------|----|
|Přepsat prioritu úlohy služby BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64ovém počítači) \Microsoft\Help\v2.3|BITSPriority|**popředí**, **Vysoká**, **normální**nebo **Nízká**|
|Nasměrování na místní úložiště obsahu v síťové sdílené složce|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v 2.3 \ Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Viz také

- [Příručka pro správce prohlížeče nápovědy](../help-viewer/administrator-guide.md)
- [Argumenty příkazového řádku pro správce obsahu pro nápovědu](../help-viewer/command-line-arguments.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)