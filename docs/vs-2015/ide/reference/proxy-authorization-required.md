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
ms.openlocfilehash: 7456e60b42b18ad706b951ee58ca5c33f05cabc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665719"
---
# <a name="proxy-authorization-required"></a>Vyžaduje se autorizace proxy serveru
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

K chybě **požadovaná autorizace proxy** většinou dochází, když jsou uživatelé připojeni k prostředkům služby Visual Studio online prostřednictvím proxy server a proxy server zablokují volání.

Pokud chcete tuto chybu opravit, zkuste jeden nebo několik následujících kroků:

- Restartujte sadu Visual Studio. Mělo by se zobrazit dialogové okno ověřování proxy. Do dialogového okna zadejte svoje přihlašovací údaje.

- Pokud výše uvedený krok problém nevyřeší, může to být způsobeno tím, že proxy server nezobrazuje výzvu k zadání přihlašovacích údajů pro http://go.microsoft.com adresy, ale pro adresy *. visualStudio.com. Pro tyto servery je nutné přidat následující adresy URL do seznamu povolených adres pro odblokování všech scénářů přihlášení v aplikaci Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- @No__t_0ovou adresu můžete ze seznamu povolených adres odebrat, aby se dialogové okno ověřování proxy serveru zobrazilo jak pro http://go.microsoft.com adresu, tak pro koncové body serveru při restartu sady Visual Studio.

- Pokud chcete použít výchozí pověření s vaším proxy serverem, udělejte toto:

   1. Vyhledejte soubor Devenv. exe. config (konfigurační soubor Devenv. exe) v souboru: **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE** (nebo **% ProgramFiles (x86)% \ Microsoft Visual Studio 14.0 \ Common7\IDE**).

   2. V konfiguračním souboru Najděte `<system.net>` blok a přidejte tento kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Vložte do `proxyaddress="<http://<yourproxy:port#>` správnou adresu proxy serveru pro vaši síť.

- Podle pokynů v [tomto příspěvku blogu](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) přidejte kód, který vám umožní používat proxy server.
