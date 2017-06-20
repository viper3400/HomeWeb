Extended Commands
=================

- Extended commands are search string starting with a double colon (::).
- The whole string is called "Command string".
- The first string after the double colon to the first appeareance of a space character ist called "Command"
- The string which follows the this space is called "Value"
- Its possible to have multiple values where each single value is separated by a semicolon

        /// Gets the command part of ExtendedCommand.
        /// </summary>
        public string Command { get { return GetCommand(this.commandString); } }
        /// <summary>
        /// Gets the first value part of ExtendendCommand.
        /// </summary>
        public string Value { get { return GetValue(this.commandString); } }
        /// <summary>
        /// Gets an array with all values of the given CommandString
        /// </summary>
        public string[] Values { get { return GetValues(this.commandString); } }
        /// <summary>
        /// Gets the whole command string. Represents the whole ExtendedCommand.
        /// </summary>
        public string CommandString { get { return this.commandString; } }  

        public ExtendedCommand(string commandString)
        {
            this.commandString = commandString;
        }