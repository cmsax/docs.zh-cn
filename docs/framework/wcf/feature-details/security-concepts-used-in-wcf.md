---
title: WCF 中使用的安全概念
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ac76f1742ab72de9f5180d1ea2fcbc668ec2140c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497628"
---
# <a name="security-concepts-used-in-wcf"></a>WCF 中使用的安全概念
Windows Communication Foundation (WCF) 安全是基于已在使用的概念和部署各种安全基础结构中。  
  
 WCF 支持一些这些基础结构，如安全套接字层 (SSL) 通过 HTTP (HTTPS)。 但是，WCF 不再仅仅是支持现有安全基础结构通过实现更高版本的可互操作安全标准 （如 Ws-security) 对 SOAP 编码消息。 无论是使用现有机制还是新的可互操作标准，其背后的安全概念都是相同的。 理解现有基础结构以及较新的标准背后的概念对于为应用程序实现最佳安全模型至关重要。  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web 服务安全简介  
 Microsoft 模式和实践组编写 WCF 安全指南即可以从此处下载了深入白皮书： [WCF 安全指南](http://go.microsoft.com/fwlink/?LinkId=210210)。 该白皮书介绍了与 Web 服务有关的基本安全概念、关键 WCF 安全概念、Intranet 应用程序方案和 Internet 应用程序方案。  
  
## <a name="industry-wide-security-specifications"></a>业界级安全规范  
  
### <a name="public-key-infrastructure"></a>公钥基础结构  
 公钥基础结构 (PKI) 是一种由数字证书、证书颁发机构以及其他注册机构所组成的系统，旨在通过使用公钥加密对电子事务中所涉及的各方进行检验和身份验证。 有关详细信息，请参阅[Windows Server 2008 R2 证书服务](http://go.microsoft.com/fwlink/?LinkId=210211)。  
  
### <a name="kerberos-protocol"></a>Kerberos 协议  
 *Kerberos 协议*是一种规范，为创建一种安全机制，对 Windows 域上的用户进行身份验证。 它允许用户建立针对域中的其他实体的安全上下文。 Windows 2000 及版本更高的平台默认情况下使用 Kerberos 协议。 在创建将与 intranet 客户端进行交互的服务时，理解系统的机制非常有用。 此外，由于*Web 服务安全性 Kerberos 绑定*的广泛发布，你可以使用 Kerberos 协议与 Internet 客户端通信 （即 Kerberos 协议是可互操作）。 有关如何在 Windows 中实现 Kerberos 协议的详细信息，请参阅[Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212)。  
  
### <a name="x509-certificates"></a>X.509 证书  
 X.509 证书是安全应用程序中使用的主要凭据形式。 有关详细信息 X.509 证书，请查看[X.509 公钥证书](http://go.microsoft.com/fwlink/?LinkId=210213)。 X.509 证书存储在证书存储区中。 运行 Windows 的计算机有多种证书存储区，每一种都针对不同的用途。 有关不同的存储的详细信息，请参阅[证书存储](http://go.microsoft.com/fwlink/?LinkID=87787)。  
  
## <a name="web-services-security-specifications"></a>Web 服务安全规范  
 系统定义的绑定支持许多常用 Web 服务安全规范。 它们支持，请参阅有关的系统提供的绑定和 web 服务规范的完整列表：[协议支持的 Web 服务系统提供的互操作性绑定](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>访问控制机制  
 WCF 提供了多种服务或操作的访问控制方式。 其中包括：  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  ASP.NET 成员身份提供程序  
  
3.  ASP.NET 角色提供程序  
  
4.  授权管理器  
  
5.  标识模型  
  
 有关详细信息这些主题，请参阅[访问控制机制](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>请参阅  
 [安全性概述](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric 的安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
