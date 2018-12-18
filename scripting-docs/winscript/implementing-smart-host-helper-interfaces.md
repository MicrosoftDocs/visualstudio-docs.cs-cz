---
title: Implementace pomocných rozhraní inteligentního hostitele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 016e2a0641772992c9c3e6f423e105c42ae20ff1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909819"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implementace pomocných rozhraní inteligentního hostitele
[Idebugdocumenthelper – rozhraní](../winscript/reference/idebugdocumenthelper-interface.md) rozhraní výrazně zjednodušuje úlohy vytvoření inteligentního hostitele pro ladění aktivní, protože obsahuje implementace pro mnoho rozhraní nutná pro inteligentní hostování.  
  
 Chcete-li být inteligentního hostitele pomocí `IDebugDocumentHelper`, hostitelské aplikace musíte udělat jenom tři věci:  
  
1. `CoCreate` Správce ladění procesu a používá [iprocessdebugmanager – rozhraní](../winscript/reference/iprocessdebugmanager-interface.md) rozhraní pro přidání aplikace do seznamu laditelné aplikací.  
  
2. Vytvoření dokumentu nápovědu ladicího programu pro každý skript objektu, použití [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) metody. Ujistěte se, že jsou definovány název dokumentu, nadřazený dokument, text a blocích skriptu.  
  
3. Implementace [iactivescriptsitedebug – rozhraní](../winscript/reference/iactivescriptsitedebug-interface.md) rozhraní na objekt, který implementuje [iactivescriptsite –](../winscript/reference/iactivescriptsite.md) rozhraní (která je potřebná pro aktivní skriptování). Pouze netriviální metodu na `IActiveScriptSiteDebug` rozhraní jednoduše deleguje do pomocné rutiny.  
  
   Volitelně můžete implementovat hostitele [idebugdocumenthost – rozhraní](../winscript/reference/idebugdocumenthost-interface.md) rozhraní, pokud ho potřebujete další kontrolu nad barvy syntaxe, vytvoření kontextu dokumentu a další rozšířené funkce.  
  
   Hlavním omezením na pomocné rutiny inteligentního hostitele je, že dokáže zpracovat pouze dokumenty, jejichž obsah změnit nebo zmenšit po byly přidány (i když můžete rozbalit dokumenty). Pro mnoho inteligentního hostitele ale funkce, které poskytuje je přesně toho, co je potřeba.  
  
   Každý krok podrobněji v následujících částech.  
  
## <a name="create-an-application-object"></a>Vytvoření objektu aplikace  
 Před použitím pomocné rutiny inteligentního hostitele, je potřeba vytvořit [idebugapplication – rozhraní](../winscript/reference/idebugapplication-interface.md) objekt reprezentující aplikaci v ladicím programu.  
  
#### <a name="to-create-an-application-object"></a>Chcete-li vytvořit objekt aplikace  
  
1.  Vytvoření instance procesu ladění pomocí správce `CoCreateInstance`.  
  
2.  Volání [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Název nastavení aplikace s použitím [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Přidání objektu aplikace do seznamu laditelné aplikací s použitím [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Následující kód popisuje proces, ale nezahrnuje kontroly chyb nebo jinými programovacími technikami robustní.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Idebugdocumenthelper – použití  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Použití pomocné rutiny (minimální posloupnost kroků)  
  
1.  Pro každý dokument hostitele, vytvořte pomocné rutiny pomocí [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Volání [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) na pomocné rutiny, uvádějí název, atributy dokumentu a tak dále.  
  
3.  Volání [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) s nadřazenou pomocné rutiny pro dokument (nebo hodnota NULL, pokud dokument je kořenový adresář) k definování pozice dokumentu ve stromové struktuře a zprůhlední ladicímu programu.  
  
4.  Volání [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) nebo [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) pro definování textového dokumentu. (Toto můžete volat vícekrát, pokud dokument se stáhne postupně jako v případě prohlížeče.)  
  
5.  Volání [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) k definování oblastí pro každý blok skriptu a přidruženého skriptovacího stroje.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Iactivescriptsitedebug – implementace  
 K implementaci [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), získat odpovídající zadanou webovou stránku pomocné rutiny a pak získat počátečního dokumentu v kontextu daného zdroje odsazení nastavte následujícím způsobem:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 V dalším kroku pomocí Pomocníka pro vytvoření nového dokumentu kontextu daného znaku posunu:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 K implementaci [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), jednoduše zavolejte `IDebugApplication::GetRootNode` (zděděno z [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 K implementaci [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), jednoduše vrátí `IDebugApplication` jste původně vytvořili pomocí Správce ladění procesu.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Volitelné idebugdocumenthost – rozhraní  
 Hostitel může poskytnout implementaci [idebugdocumenthost – rozhraní](../winscript/reference/idebugdocumenthost-interface.md) pomocí [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) nabízí větší kontrolu nad pomocné rutiny. Tady jsou některé z klíčových věcí rozhraní hostitele umožňuje provádět:  
  
-   Přidání pomocí textu [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) tak, aby hostitel není nutné poskytnout skutečnými znaky okamžitě. Pokud znaky jsou ve skutečnosti nepotřebujete, bude volat pomocné rutiny [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) na hostiteli.  
  
-   Přepište výchozí barevné zvýrazňování syntaxe poskytuje pomocné rutiny. Volání pomocné rutiny [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) k určení barevné zvýraznění pro rozsah znaků návrat na jeho výchozí implementace, pokud hostitel `E_NOTIMPL`.  
  
-   Zadejte řídící neznámou dokumentu kontextů vytvořené pomocné rutiny implementací [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). To umožňuje hostiteli přepsání funkce výchozí implementaci kontextu dokumentu.  
  
-   Zadejte název cesty v systému souborů pro dokument. Některé ladění uživatelských rozhraní pomocí to umožňující uživateli upravit a uložit změny do dokumentu. [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) se volá se, aby upozornil hostitele po uložení dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ladění aktivních skriptů](../winscript/active-script-debugging-overview.md)