---
title: 'Řešení potíží s výjimkami: System.ServiceModel.Security.MessageSecurityException | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e7d13f5cc282026b1590f59180ed7f25312bb926
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742482"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Řešení potíží s výjimkami: System.ServiceModel.Security.MessageSecurityException
A <xref:System.ServiceModel.Security.MessageSecurityException> výjimka je vyvolána, když [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] Určuje, že zpráva není správně zabezpečené nebo nebude bylo manipulováno. Dojde k chybě nejčastěji Pokud jsou splněny všechny následující podmínky:  
  
-   Pomocí odkazu na službu WCF prostřednictvím vzdáleného připojení, jako je připojení ke vzdálené ploše nebo Terminálovými službami komunikovat se službou WCF (.svc) v projektu webové stránky nebo webové aplikace.  
  
-   Nemáte oprávnění správce na vzdáleném serveru.  
  
-   Právě zpracovávají požadavky na místního hostitele vzdálené lokality [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vývojový Server.  
  
## <a name="associated-tips"></a>Přidružené tipy  
 **Při použití serveru ASP.Net Development Server, vyřešte potíže s ověřováním NTLM.**  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Vývojový Server má obvykle vypnuté, zabezpečení systému Windows NT požadavku a odpovědi (NTLM), což umožňuje anonymní přístup. Ve výchozím nastavení je při spuštění relace Terminálové služby nebo používání vzdáleného připojení povoleno zabezpečení NTLM. Když je povolený protokol NTLM, se ověří všechny požadavky na místního hostitele s přihlašovacími údaji uživatele nebo proces, který spustil [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vývojový Server. To snižuje bezpečnostní hrozby. Ale WCF také provádí vlastní ověřování a neumožňuje účet bez oprávnění správce k využívání služeb WCF.  
  
 Pokud vzdálený uživatel může být spuštěn na webu pomocí [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vývojový Server a také pracovat s webovou službu nebo službu WCF, můžete buď vytvořit vazbu vlastního služby, nebo vypnout zabezpečení NTLM.  
  
> [!IMPORTANT]
>  Vypnutí zabezpečení NTLM se nedoporučuje a může představovat bezpečnostní hrozbu.  
  
 Pokud vytvoříte vlastní službu vazby, jsou chráněny stále ověřování protokolem NTLM.  
  
 Použijte následující postup k vytvoření vazby vlastní služby pro službu WCF.  
  
#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>Pokud chcete vytvořit vlastní službu vazeb pro služby WCF hostované uvnitř serveru ASP.NET Development Server  
  
1. Otevřete soubor Web.config pro službu WCF, která vygenerovala výjimku.  
  
2. Zadejte následující informace do souboru Web.config.  
  
   ```  
   <bindings>  
     <customBinding>  
       <binding name="Service1Binding">  
         <transactionFlow />  
         <textMessageEncoding />  
         <httpTransport authenticationScheme="Ntlm" />  
       </binding>  
     </customBinding>  
   </bindings>  
   ```  
  
3. Uložte a zavřete soubor Web.config.  
  
4. Kód služby WCF nebo Web změňte hodnotu koncového bodu takto:  
  
   ```  
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
   ```  
  
    Tím se zajistí, že služba používá vlastní vazby.  
  
5. Přidejte odkaz na službu ve webové aplikaci, která přistupuje k službě. (V **přidat odkaz na službu** dialogovém okně přidejte odkaz na službu, jako jste to udělali s původní služby, který se generuje výjimku.)  
  
   Provedením následujících kroků zakázat zabezpečení NTLM, když pracujete s odkaz na službu WCF.  
  
> [!IMPORTANT]
>  Vypnutí zabezpečení NTLM se nedoporučuje a může představovat bezpečnostní hrozbu.  
  
#### <a name="to-turn-off-ntlm-security"></a>Chcete-li vypnout zabezpečení NTLM  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název webového serveru a potom klikněte na tlačítko **stránky vlastností**.  
  
2.  Vyberte **možnosti spuštění**a poté zrušte zaškrtnutí **ověřování protokolem NTLM** zaškrtávací políčko.  
  
3.  Klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Použití Pomocníka pro výjimky](http://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)