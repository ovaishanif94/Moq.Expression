# Moq.Expression
This package helps you to solve expression function in unit test moq framework.

[![GitHub license](https://img.shields.io/github/license/ovaishanif94/Moq.Expression.svg)](https://github.com/ovaishanif94/Moq.Expression/blob/master/LICENSE)  [![Nuget downloads](https://img.shields.io/nuget/dt/MoqExpression.svg)](https://www.nuget.org/packages/MoqExpression/) [![Nuget version](https://img.shields.io/nuget/v/MoqExpression.svg)](https://www.nuget.org/packages/MoqExpression/) [![GitHub issues](https://img.shields.io/github/issues/ovaishanif94/Moq.Expression.svg)](https://GitHub.com/ovaishanif94/Moq.Expression/issues/) [![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/ovaishanif94/Moq.Expression/graphs/commit-activity)

### Download
The latest stable release is available on NuGet: https://www.nuget.org/packages/MoqExpression/

#### Example
`Install-Package MoqExpression -Version 2.0.0`

**IUserService**

    public class User
    {
        public string UserId { get; set; }
        public string Name { get; set; }
    }

    public interface IUserService
    {
        User FindByUserId(Expression<Func<User, bool>> expression);
    }

**UnitTest**

    using MoqExpression;

    User user = new User();
    Mock<IUserService> mockUserService = new Mock<IUserService>();
    mockUserService.Setup(x => x.FindByUserId(MoqHelper.IsExpression<User>(s => s.UserId.Equals("123")))).Returns(user);

**Note: Make sure don't use like this, it will not work.**

    // don't use like this it will not work 
    Expression<Func<User, bool>> expression = MoqHelper.IsExpression<User>(s => s.UserId.Equals("123"));
    mockUserService.Setup(x => x.FindByUserId(expression)).Returns(user);

    // use equal function instead of ==
    mockUserService.Setup(x => x.FindByUserId(MoqHelper.IsExpression<User>(s => s.UserId == "123"))).Returns(user);
    
# Buy me a coffee :coffee:

ETH: 0xC32Cce6e9A2C88fBe77430B94306C2Db443c06d4

BTC: 1MWVz2MFuHrnTfzxZ8GUSiZXgKuTuRHNLW

BCH: bitcoincash:qr8xav6nzhaj2l9xutvhps36sgxcn8nknge0jz567s
