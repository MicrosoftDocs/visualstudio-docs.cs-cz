---
title: Instalace a použití Visual Studia pro Mac za bránou firewall nebo proxy serverem
description: Tento dokument obsahuje seznam hostitelů, které musí být povoleny ve vaší bráně firewall, aby Visual Studio pro Mac (a jeho úlohy, včetně Xamarin) pracovat v podnikovém prostředí.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 10/23/2018
ms.openlocfilehash: 738c5277ca6a669a834635f5c626e0cbabd7a7ef
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984940"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalace a použití Visual Studia pro Mac za bránou firewall nebo proxy serverem

Pokud vy nebo vaše organizace používáte bezpečnostní opatření, jako je brána firewall nebo proxy server, pak existují domény, které můžete chtít přidat do seznamu povolených položek a porty a protokoly, které budete chtít otevřít, abyste měli nejlepší zkušenosti při instalaci a použití Visual Studio pro Mac a Služby Azure.

- [**Instalace Visual Studia pro Mac**](#install-visual-studio-for-mac): Tyto tabulky obsahují domény, které musí umožňovat připojení, abyste měli přístup ke všem funkcím a úlohám Visual Studia for Mac.

- [**Použití visual studia pro Mac**](#use-visual-studio-for-mac): Tyto tabulky obsahují domény, které musí umožňovat připojení, abyste měli přístup k souvisejícím funkcím.

## <a name="install-visual-studio-for-mac"></a>Instalace sady Visual Studio pro Mac

Vzhledem k tomu, že instalační služba sady Visual Studio for Mac se stahuje z různých domén a serverů pro stahování, tady jsou domény a adresy URL, které můžete chtít přidat jako důvěryhodné v konfiguracích.

### <a name="microsoft-domains"></a>Domény Společnosti Microsoft

| Domain (Doména)| Účel |
| ----------------------------------- |---------------------------|
| *.live.com| Správa pověření |
| app.vssps.visualstudio.com| Metadata instalačního programu|
| vortex.data.microsoft.com | Zasílání zpráv o selhání a chybách |
| az667904.vo.msecnd.net| Zasílání zpráv o selhání a chybách |
| xamarin.com | Metadata instalačního programu|
| xampubdl.blob.core.windows.net| Instalační balíčky|
| download.visualstudio.microsoft.com | Instalační balíčky|
| xamarin.azureedge.net | Instalační balíčky|
| developer.xamarin.com | Instalační balíčky|
| dc.services.visualstudio.com| Hlášení selhání |

### <a name="third-party-domains"></a>Domény třetích stran

| Domain (Doména)| Účel |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Bezpečnostní služby Apple |

## <a name="use-visual-studio-for-mac"></a>Použití Visual Studia pro Mac

Chcete-li se ujistit, že máte přístup ke všem funkcím, které potřebujete v sadě Visual Studio for Mac za proxy nebo bránou firewall, doporučujeme přidat následující domény a porty do seznamu povolených přístupů.

### <a name="general"></a>Obecné

| Domain (Doména) | Port(y)|Účel|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Řešení adres URL společnosti Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Data úvodní stránky|
| software.xamarin.com |  80/443|Služba aktualizačního programu|
| addins.monodevelop.com | 80/443| Rozšiřující služby |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Experimentální funkce a oznámení |
| targetednotifications.azurewebsites.net|  80/443| Slouží k filtrování globálního seznamu oznámení do seznamu, který je použitelný pouze pro určité typy počítačů/scénářů použití.|

### <a name="identity"></a>Identita

| Domain (Doména) | Port(y)|Účel|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Zprostředkovatel identity|
| secure.aadcdn.microsoftonline-p.com | 80/443|Zprostředkovatel identity|
| dc.services.visualstudio.com| 80/443|Hlášení selhání|
| management.azure.com|80/443| Rozhraní API služeb Azure |

### <a name="nuget"></a>NuGet

| Domain (Doména) | Port(y)|Účel|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|NuGet API|
| secure.aadcdn.microsoftonline-p.com |80/443| Zprostředkovatel identity|

### <a name="android-projects"></a>Android projekty

| Domain (Doména)| Účel|
| ------------------------------------|------------------------------------|
| time.android.com| Časový server pro emulátor Androidu |
| connectivitycheck.gstatic.com | Konektivita pro emulátor Androidu|
| cloudconfig.googleapis.com| API pro emulátor Androidu|

## <a name="see-also"></a>Viz také

- [Instalace a používání Visual Studia 2017 a Služeb Azure za bránou firewall nebo proxy serverem](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Řešení podobných problémů ve Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
