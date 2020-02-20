---
title: 'Postupy: povolení ladění pro aplikace ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726e964a0db2fae1b902f54a14e206dbc03a148
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477013"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Postupy: Povolení ladění pro aplikace ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li povolit ladění, je nutné jej povolit na stránce **vlastností projektu** i v souboru Web. config aplikace.  
  
> [!NOTE]  
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](/previous-versions/zbhkx167(v=vs.140)).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Povolení ladění ASP.NET ve vlastnostech projektu (jazyk Visual Basic nebo C#)  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název webového projektu a vyberte možnost **vlastnosti**.  
  
2. Na stránce vlastností projektu klikněte na kartu **Web** .  
  
3. V části **ladicí programy**zaškrtněte políčko **ASP.NET** .  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Povolení ladění v souboru web.config  
  
1. Otevřete soubor web.config použitím standardního textového editoru nebo parseru XML.  
  
    > [!NOTE]  
    > K souboru však nelze přistupovat vzdáleně pomocí webového prohlížeče. Z bezpečnostních důvodů konfiguruje [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] službu Microsoft IIS pro zabránění přímého přístupu prohlížeče k souborům Web.config. Jestliže se pokusíte přistoupit ke konfiguračnímu souboru z prohlížeče, zobrazí se chyba přístupu protokolu HTTP 403 (zakázáno).  
  
2. Soubor web.config je soubor XML, obsahuje proto vnořené oddíly označené značkami. Vyhledejte element `configuration/system.web/compilation`. Pokud element compilation neexistuje, vytvořte jej.  
  
3. Pokud element `compilation` neobsahuje atribut `debug`, přidejte tento atribut do elementu.  
  
4. Ujistěte se, že je hodnota atributu `debug` nastavena na `true`.  
  
Soubor web.config by měl vypadat jako následující příklad. Mezi elementy configuration a system.web mohou být oddíly.  
  
- oddíly elementů mezi elementy configuration a system.web  
  
- oddíly elementů mezi elementy system.web a compilation  
  
- Element compilation může obsahovat jiné atributy a elementy  
  
## <a name="example"></a>Příklad  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Robustní programování  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] automaticky detekuje všechny změny v souborech Web. config a aplikuje nové nastavení konfigurace. Změny se projeví až po restartování počítače nebo restartování serveru služby IIS.  
  
Webová stránka může obsahovat více virtuálních adresářů a podadresářů a soubory Web.config mohou existovat v každém z nich. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace dědí nastavení ze souborů Web. config na vyšších úrovních v cestě URL. Hierarchické konfigurační soubory umožňují změnit nastavení pro několik aplikací [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] současně, jako například pro všechny aplikace v hierarchii pod ní. Je-li však element `debug` nastaven v souboru v nižší hierarchii, přepíše vyšší hodnotu.  
  
Můžete například zadat `debug="true"` v `www.microsoft.com/aaa/Web.config`a libovolná aplikace ve složce AAA nebo v jakékoli podsložce AAA zdědí toto nastavení. Takže pokud je vaše aplikace [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] v `www.microsoft.com/aaa/bbb`, zdědí toto nastavení, stejně jako všechny [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace v `www.microsoft.com/aaa/ccc`, `www.microsoft.com/aaa/ddd`a tak dále. Jedinou výjimkou je, pokud jedna z těchto aplikací přepíše nastavení pomocí vlastního nižšího souboru Web.config.  
  
Povolení ladění výrazně ovlivní výkon aplikace [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Nezapomeňte vypnout režim ladění před nasazením vydání aplikace nebo před měřením výkonu.  
  
## <a name="see-also"></a>Viz také  
[Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
