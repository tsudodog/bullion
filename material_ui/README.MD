# Material UI
  Honestly one of my favourite web component libraries to use, however, it does have some rough spots.
  
  
  
## Styling

### Switch Component

```
import React, { useState } from "react";
import { makeStyles } from "@material-ui/core/styles";
import Radio from "@material-ui/core/Radio";
import RadioGroup from "@material-ui/core/RadioGroup";
import FormControlLabel from "@material-ui/core/FormControlLabel";
import FormControl from "@material-ui/core/FormControl";
import InputLabel from "@material-ui/core/InputLabel";
import MenuItem from "@material-ui/core/MenuItem";
import Select from "@material-ui/core/Select";
import PropTypes from "prop-types";
import Typography from "@material-ui/core/Typography";
import clsx from "clsx";
const useStyles = makeStyles((theme) => ({
  bg: {
    backgroundColor: "black"
  },
  selectRoot: {
    color: "white",
    "& .MuiOutlinedInput-notchedOutline": {
      borderColor: "#DDDDDD"
    },
    "&:hover .MuiOutlinedInput-notchedOutline": {
      borderColor: "#ffffff"
    },
    "&:active .MuiOutlinedInput-notchedOutline": {
      borderColor: "#ffffff"
    },

    "&:hover": {
      borderColor: "#ffffff"
    },

    "&.MuiOutlinedInput-root.Mui-focused .MuiOutlinedInput-notchedOutline": {
      borderColor: "#ffffff"
    },
    "&.MuiSelect-icon": {
      color: "white"
    },
    // disabled styles
    "&.MuiOutlinedInput-root.Mui-disabled .MuiOutlinedInput-notchedOutline": {
      borderColor: "#BBBBBB"
    },
    "& .MuiSelect-icon.Mui-disabled": {
      color: "#BBBBBB"
    },
    "& .MuiFormLabel-root.Mui-disabled": {
      color: "#BBBBBB"
    }
  },
  labelRoot: {
    marginLeft: "10px",
    color: "white",

    // disabled styles
    "&.MuiFormLabel-root.Mui-disabled": {
      color: "#BBBBBB"
    },
    "&.MuiFormLabel-root.Mui-focused": {
      color: "#ffffff"
    }
  },
  notchedOutline: {}
}));

export const CustomSelect = (props) => {
  const classes = useStyles();

  const [time, setTime] = useState("");
  const [value, setValue] = useState("");
  const [error, setError] = useState(false);
  const [isEnabled, setIsEnabled] = useState(false);

  const handleChange = (event) => {
    setTime(event.target.value);
  };
  const handleRadioChange = (event) => {
    console.log(event);
    const value = event.target.value;
    console.log(value);
    setValue(value);
    if (value === "auto") {
      setIsEnabled(true);
    } else if (value === "manual") {
      setIsEnabled(false);
      setTime("");
    } else {
      console.error("An incorrect value was set.");
    }
    setError(false);
  };
  return (
    <div className={classes.bg}>
      <FormControl>
        <RadioGroup
          row
          aria-label="quiz"
          name="quiz"
          value={value}
          onChange={handleRadioChange}
        >
          <FormControlLabel
            value="auto"
            control={<Radio/>}
            label={<Typography>Enable Switch</Typography>}
          />
          <FormControlLabel
            value="manual"
            control={<Radio/>}
            label={<Typography>Disable Switch</Typography>}
          />
        </RadioGroup>
      </FormControl>
      <div>
        <FormControl style={{ width: "200px" }} disabled={!isEnabled}>
          <InputLabel className={clsx(classes.labelRoot)}>
            Delay Time
          </InputLabel>
          <Select
            variant="outlined"
            className={clsx(classes.selectRoot)}
            value={time}
            onChange={handleChange}
          >
            <MenuItem value={0}>None</MenuItem>
            <MenuItem value={30}>Label 1</MenuItem>
            <MenuItem value={60}>LAbel 2</MenuItem>
            <MenuItem value={120}>Lable 3</MenuItem>
          </Select>
        </FormControl>
      </div>
    </div>
  );
};

export default CustomSelect;


```
