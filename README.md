### Getting Started

In this libary module will provide a custom, moduler UI authentication given below here:

### Features

-   [x] Login Via Password
-   [x] Forgot Password
-   [x] Reset Password
-   [ ] Login Via OTP
-   [x] Verify OTP

[Example Git Url](https://github.com/deepanshuhsaini653/root-application)

# Login Featrue

Login feature is working fine now.

### Login Props

```reactjs
ILoginViaPasswordProps {
  fieldConfig?: IFeild;
  fieldGutter?: number;
  buttonConfig?: any;
  loader?: boolean;
  subHead?: string;
  onSubmitData?: (data: IFormInputs) => void | undefined;
  redirectToForgotPassword?: () => void | undefined;
  hideForgotPassword?: boolean;
  hideRememberMe?: boolean;
}
```

### Example:

```reactjs
import React, { useState } from "react";
import { useNavigate } from "react-router";
import { LoginViaPassword } from "react-mat-authentication";

const LoginComponent = () => {
  const [loader, setLoader] = useState(false);
  const navigate = useNavigate();

  const redirectToForgotPasswordHandler = () => navigate("/forgot-password");

  return (
    <LoginViaPassword
      fieldConfig={{ variant: "outlined" }}
      loader={loader}
      hideForgotPassword={true}
      hideRememberMe={true}
      onSubmitData={(data: any) => {
        console.log(data);
        setLoader(true);
        setTimeout(() => {
          setLoader(false);
        }, 1000);
      }}
      redirectToForgotPassword={redirectToForgotPasswordHandler}
    />
  );
};

export const Login = LoginComponent;
```

# Forgot Password Feature

Forgot password feature is working fine now.

### Forgot Password Props

```reactjs
IForgotPasswordProps {
  type: "mobile" | "email";
  isCode?: boolean;
  fieldConfig?: IFeild;
  buttonConfig?: any;
  loader?: boolean;
  onSubmitData: (data: any) => any;
  redirectToSignIn: () => void | undefined;
}
```

### Example:

```reactjs
import React, { useState } from "react";
import { useNavigate } from "react-router";
import { ForgotPassword } from "react-mat-authentication";

const ForgotPasswordComponent = () => {
  const [loader, setLoader] = useState(false);
  const navigate = useNavigate();
  const redirectToSigninHandler = () => navigate("/login");

  return (
    <div>
      <ForgotPassword
        type="mobile"
        loader={loader}
        onSubmitData={(data: any) => {
          console.log(data);
          setLoader(true);
          setTimeout(() => {
            setLoader(false);
            navigate("/reset-password");
          }, 1000);
        }}
        redirectToSignIn={redirectToSigninHandler}
      />
    </div>
  );
};

export const ForgotPasswordPage = ForgotPasswordComponent;
```

# Reset Password Feature

Reset password feature is working fine now.

### Reset Password Props

```reactjs
IResetPasswordProps {
  fieldConfig?: IFeild;
  loader?: boolean;
  buttonConfig?: any;
  onSubmitData: (data: IFormInputs) => void | undefined;
  redirectToSignIn: () => void | undefined;
}

```

### Example:

```reactjs
import React, { useState } from "react";
import { useNavigate } from "react-router";
import { ResetPassword } from "react-mat-authentication";

export default function ResetPasswordPage() {
  const [loader, setLoader] = useState(false);
  const navigate = useNavigate();
  const redirectToSigninHandler = () => navigate("/login");

  return (
    <div>
      <ResetPassword
        loader={loader}
        onSubmitData={(data: any) => {
          console.log(data);
          setLoader(true);
          setTimeout(() => {
            setLoader(false);
            navigate("/reset-password");
          }, 1000);
        }}
        redirectToSignIn={redirectToSigninHandler}
      />
    </div>
  );
}
```

# Verify OTP Feature

Verify OTP feature is working fine now.

### Verify OTP Props

```reactjs
IVerifyOTPProps {
  buttonConfig?: any;
  loader?: boolean;
  numInputs?: number;
  otpDuration?: number;
  isInputNum?: boolean;
  subHead?: string;
  onSubmitData: (data: string) => void | undefined;
  resendOTPData: () => void | undefined;
}
```

### Example:

```reactjs
import React from "react";
import { VerifiOTP } from "react-mat-authentication";

export const VerifiOTPScreen = () => {
  const [loader, setLoader] = React.useState(false);

  const resendOtpHandler = () => {};

  const submitHandler = (data: any) => {
    console.log(data);
    setLoader(true);
    setTimeout(() => {
      setLoader(false);
    }, 1000);
  };

  return (
    <div>
      <VerifiOTP
        loader={loader}
        isInputNum={false}
        numInputs={6}
        otpDuration={5}
        resendOTPData={resendOtpHandler}
        onSubmitData={submitHandler}
      />
    </div>
  );
};
```

# Add this CSS

```css
Use this css .otpContainer {
    display: flex;
}

.otpInput {
    width: 100% !important;
    height: 3rem;
    margin: 0 1rem;
    font-size: 2rem;
    text-align: center;
    border: none;
    outline: 0;
    border-bottom: 1px solid rgba(0, 0, 0, 0.3);
}

.otpInput::-webkit-outer-spin-button,
.otpInput::-webkit-inner-spin-button {
    -webkit-appearance: none;
}

/*  Add breakpoint for iPhone */
@media only screen and (max-width: 375px) {
    .otpInput {
        width: 100% !important;
        height: 1.5rem;
        font-size: 1rem;
        padding: 8px;
    }
}
```
