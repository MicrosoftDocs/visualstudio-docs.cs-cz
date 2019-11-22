---
title: Vyžaduje se autorizace proxy serveru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297816"
---
# <a name="proxy-authorization-required"></a>Vyžaduje se autorizace proxy serveru
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

K chybě **požadovaná autorizace proxy** většinou dochází, když jsou uživatelé připojeni k prostředkům služby Visual Studio online prostřednictvím proxy server a proxy server zablokují volání.

Pokud chcete tuto chybu opravit, zkuste jeden nebo několik následujících kroků:

- Restartujte sadu Visual Studio. By se zobrazit dialogové okno ověřování proxy serveru. Do dialogového okna zadejte svoje přihlašovací údaje.

- Pokud výše uvedený krok problém nevyřeší, může to být způsobeno tím, že proxy server nezobrazuje výzvu k zadání přihlašovacích údajů pro https://go.microsoft.com adresy, ale pro adresy *. visualStudio.com. Pro tyto servery je nutné přidat následující adresy URL do seznamu povolených adres pro odblokování všech scénářů přihlášení v aplikaci Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- https://go.microsoft.comovou adresu můžete ze seznamu povolených adres odebrat, aby se dialogové okno ověřování proxy serveru zobrazilo jak pro https://go.microsoft.com adresu, tak pro koncové body serveru při restartu sady Visual Studio.

- Pokud chcete použít výchozí pověření s vaším proxy serverem, udělejte toto:

   1. Vyhledejte soubor Devenv. exe. config (konfigurační soubor Devenv. exe) v souboru: **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE** (nebo **% ProgramFiles (x86)% \ Microsoft Visual Studio 14.0 \ Common7\IDE**).

   2. V konfiguračním souboru Najděte `<system.net>` blok a přidejte tento kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Vložte do `proxyaddress="<http://<yourproxy:port#>`správnou adresu proxy serveru pro vaši síť.

- Podle pokynů v [tomto příspěvku blogu](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) přidejte kód, který vám umožní používat proxy server.
