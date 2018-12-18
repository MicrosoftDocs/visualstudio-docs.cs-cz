---
title: 'Postupy: povolení ladění pro aplikace ASP.NET | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: c199e03af8a21b3134ae0e2afac7bd9b153be2f4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749120"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Postupy: Povolení ladění pro aplikace ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete povolit ladění, je nutné ho povolit jak **vlastnosti projektu** stránky a v souboru web.config aplikace.  
  
> [!NOTE]  
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Povolení ladění ASP.NET ve vlastnostech projektu (jazyk Visual Basic nebo C#)  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název webového projektu a vyberte **vlastnosti**.  
  
2.  Na stránce vlastností projektu klikněte na tlačítko **webové** kartu.  
  
3.  V části **ladicí programy**, vyberte **ASP.NET** zaškrtávací políčko.  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Povolení ladění v souboru web.config  
  
1.  Otevřete soubor web.config použitím standardního textového editoru nebo parseru XML.  
  
    > [!NOTE]  
    > K souboru však nelze přistupovat vzdáleně pomocí webového prohlížeče. Z bezpečnostních důvodů konfiguruje [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] službu Microsoft IIS pro zabránění přímého přístupu prohlížeče k souborům Web.config. Jestliže se pokusíte přistoupit ke konfiguračnímu souboru z prohlížeče, zobrazí se chyba přístupu protokolu HTTP 403 (zakázáno).  
  
2.  Soubor web.config je soubor XML, obsahuje proto vnořené oddíly označené značkami. Vyhledejte element `configuration/system.web/compilation`. Pokud element compilation neexistuje, vytvořte jej.  
  
3.  Pokud element `compilation` neobsahuje atribut `debug`, přidejte tento atribut do elementu.  
  
4.  Ujistěte se, že je hodnota atributu `debug` nastavena na `true`.  
  
Soubor web.config by měl vypadat jako následující příklad. Mezi elementy configuration a system.web mohou být oddíly.  
  
-   oddíly elementů mezi elementy configuration a system.web  
  
-   oddíly elementů mezi elementy system.web a compilation  
  
-   Element compilation může obsahovat jiné atributy a elementy  
  
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
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] automaticky detekuje jakékoli změny v souboru Web.config a aplikuje nové nastavení konfigurace. Není nutné restartovat počítač nebo restartujte server IIS se změny projevily.  
  
Webová stránka může obsahovat více virtuálních adresářů a podadresářů a soubory Web.config mohou existovat v každém z nich. Aplikace [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] dědí nastavení ze souborů Web.config, které jsou v cestě adresy URL výše. Hierarchické konfigurační soubory umožňují změnit nastavení pro několik aplikací [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] současně, jako například pro všechny aplikace v hierarchii pod ní. Je-li však element `debug` nastaven v souboru v nižší hierarchii, přepíše vyšší hodnotu.  
  
Například lze zadat `debug="true"` v www.microsoft.com/aaa/Web.config a jakékoli aplikace ve složce aaa nebo v libovolné podsložce aaa zdědí toto nastavení. Takže je-li aplikace [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] na www.microsoft.com/aaa/bbb, zdědí toto nastavení, stejně jako aplikace [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] v www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd a tak dále. Jedinou výjimkou je, pokud jedna z těchto aplikací přepíše nastavení pomocí vlastního nižšího souboru Web.config.  
  
Povolení ladění výrazně ovlivní výkon aplikace [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Nezapomeňte vypnout režim ladění před nasazením vydání aplikace nebo před měřením výkonu.  
  
## <a name="see-also"></a>Viz také  
[Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
  




