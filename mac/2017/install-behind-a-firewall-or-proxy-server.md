---
title: Instalace a použití Visual Studio pro Mac za bránou firewall nebo proxy server
description: Tento dokument obsahuje seznam hostitelů, které musí být v bráně firewall povolené, aby bylo možné Visual Studio pro Mac (a jeho zatížení, včetně Xamarin) pro práci v podnikovém prostředí.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 10/23/2018
ms.openlocfilehash: 738c5277ca6a669a834635f5c626e0cbabd7a7ef
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984940"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalace a použití Visual Studio pro Mac za bránou firewall nebo proxy server

Pokud vy nebo vaše organizace používáte bezpečnostní opatření, jako je brána firewall nebo proxy server, pak jsou domény, které byste mohli chtít přidat do seznamu povolených portů, a porty a protokoly, které byste mohli chtít otevřít, abyste měli k dispozici nejlepší prostředí při instalaci a používání služby VIS Protokolování přístupu uživatele Studio pro Mac a služby Azure.

- [**Instalace Visual Studio pro Mac**](#install-visual-studio-for-mac): tyto tabulky obsahují domény, které musí umožňovat připojení, abyste měli přístup ke všem funkcím a úlohám Visual Studio pro Mac.

- [**Použití Visual Studio pro Mac**](#use-visual-studio-for-mac): tyto tabulky obsahují domény, které musí umožňovat připojení, abyste měli přístup k souvisejícím funkcím.

## <a name="install-visual-studio-for-mac"></a>Instalace sady Visual Studio pro Mac

Vzhledem k tomu, že instalační program Visual Studio pro Mac stahuje z různých domén a stahuje servery, tady jsou domény a adresy URL, které můžete chtít přidat jako důvěryhodné ve vašich konfiguracích.

### <a name="microsoft-domains"></a>Microsoft domains

| Doména| Účel |
| ----------------------------------- |---------------------------|
| *.live.com| Správa pověření |
| app.vssps.visualstudio.com| Metadata instalačního programu|
| vortex.data.microsoft.com | Chybové hlášení chyb a chyb |
| az667904.vo.msecnd.net| Chybové hlášení chyb a chyb |
| xamarin.com | Metadata instalačního programu|
| xampubdl.blob.core.windows.net| Instalační balíčky|
| download.visualstudio.microsoft.com | Instalační balíčky|
| xamarin.azureedge.net | Instalační balíčky|
| developer.xamarin.com | Instalační balíčky|
| dc.services.visualstudio.com| Oznamování chyb |

### <a name="third-party-domains"></a>Domény třetích stran

| Doména| Účel |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Služby Apple Security |

## <a name="use-visual-studio-for-mac"></a>Použít Visual Studio pro Mac

Abyste se ujistili, že máte přístup ke všem funkcím, které potřebujete v Visual Studio pro Mac za proxy serverem nebo bránou firewall, doporučujeme přidat následující domény a porty do seznamu povolených přístupů.

### <a name="general"></a>Obecné

| Doména | Port(y)|Účel|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Překlad adresy URL Microsoftu |
| vsstartpage.blob.core.windows.net| 80/443| Data počáteční stránky|
| software.xamarin.com |  80/443|Aktualizační služba|
| addins.monodevelop.com | 80/443| Služby rozšíření |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Experimentální funkce a oznámení |
| targetednotifications.azurewebsites.net|  80/443| Slouží k filtrování globální seznam oznámení do seznamu, který se vztahuje pouze na konkrétní typy počítačů nebo použití scénáře|

### <a name="identity"></a>Identita

| Doména | Port(y)|Účel|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Zprostředkovatel identity|
| secure.aadcdn.microsoftonline-p.com | 80/443|Zprostředkovatel identity|
| dc.services.visualstudio.com| 80/443|Oznamování chyb|
| management.azure.com|80/443| Rozhraní API služeb Azure |

### <a name="nuget"></a>NuGet

| Doména | Port(y)|Účel|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| Zprostředkovatel identity|

### <a name="android-projects"></a>Projekty pro Android

| Doména| Účel|
| ------------------------------------|------------------------------------|
| time.android.com| Časový server pro Android Emulator |
| connectivitycheck.gstatic.com | Připojení pro Android Emulator|
| cloudconfig.googleapis.com| Rozhraní API pro Android Emulator|

## <a name="see-also"></a>Viz také:

- [Instalace a použití služeb Visual Studio 2017 a Azure za bránou firewall nebo proxy server](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Řešení podobných potíží ve Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
